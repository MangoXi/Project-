#include <cstdlib>
#include <cstdio>
#include <cstdint>
#include <cstring>
#include <cstdbool>

typedef enum _Sex
{
	MALE,
	FEMALE
}Sex;

typedef struct _Node
{
	char name[256];
	int  salary;
	Sex  sex;
	struct _Node* next;
} Node, *NodePtr;

void processList(NodePtr list);
bool isEmpty(NodePtr list);
int insertData(NodePtr *ppNode, const char* data);
int appendData(NodePtr *ppNode, const char* data);
int deleteData(NodePtr *ppNode, const char* data);
void findData(NodePtr list, const char* name);
int enterChoice(void);

int main()
{
	NodePtr header = 0;
	Node* pCurNode = header;

	char name[256];
	while (1)
	{
		int choice = enterChoice();
		switch (choice)
		{
		case 1:
		{
			fputs("input name:\n", stdout);
			memset(name, 0, 256);
			scanf("%s", name);
			appendData(&header, name);
		}
		break;
		case 2:
		{
			fputs("input the name(delete):\n", stdout);
			memset(name, 0, 256);
			scanf("%s", name);
			deleteData(&header, name);
		}
		break;
		case 3:
		{
			fputs("input the name to show:\n", stdout);
			memset(name, 0, 256);
			scanf("%s", name);
			//printf("%s", name);
			findData(header, name);
		}
		break;
		case 4:
		{
			fputs("list contents:\n", stdout);
			processList(header);
		}
		break;
		default:
			printf("Thanks for your use!\n");
			return 0;
		}
	}
	return 0;
}

void processList(NodePtr list)
{
	Node* pNode = list;
	int row = 1;
	while (pNode != 0)
	{
		printf(":%d\t%s\n", row, pNode->name);
		pNode = pNode->next;
		row++;
	}
	fputs("\n", stdout);
}

bool isEmpty(NodePtr list)
{
	return list == 0;
}

int insertData(NodePtr *ppNode, const char* data)
{
	char* a = NULL; 
	a = (char*)malloc(100 * sizeof(char));
	NodePtr pCurNode = *ppNode;
	if (pCurNode == 0) 
	{
		*ppNode = (NodePtr)malloc(sizeof(Node));
		memset(*ppNode, 0, sizeof(Node));
		pCurNode = *ppNode;
	}
	else
	{
		Node* pNewNode = (Node*)malloc(sizeof(Node));
		memset(pNewNode, 0, sizeof(Node));
		pNewNode->next = pCurNode->next;
		pCurNode->next = pNewNode;//3. 
		pCurNode = pNewNode;
	}
	free(a);
	strcpy(pCurNode->name, data);
	sprintf(a, "%s", pCurNode->name);
	return 0;
}

/**
* 从指定节点后追加节点，并将数据赋值给这个节点。
* 1. 如果列表为空，生成新节点， 赋值
* 2. 直到到达列表末端，生成新节点
*
* @author zf (09/01/2017)
*
* @param NodePtr   列表头节点指针
*
* @param const char*   数据
*
* @return int  失败返回-1， 成功返回0
*/

int appendData(NodePtr *ppNode, const char* data)
{
	if (*ppNode == 0)
	{
		return insertData(ppNode, data);
	}
	NodePtr pNode = *ppNode;
	while (pNode->next != 0)
	{
		pNode = pNode->next;
	}
	Node* pNewNode = (Node*)malloc(sizeof(Node));
	if (pNewNode == 0)
	{
		return -1;
	}
	memset(pNewNode, 0, sizeof(Node));
	pNode->next = pNewNode;
	strcpy(pNewNode->name, data);

	return 0;
}

int deleteData(NodePtr *ppNode, const char* data)
{
	if (ppNode == 0 || *ppNode == 0)
	{
		return -1;
	}
	NodePtr pNode = *ppNode;
	NodePtr preNode = 0;
	while (pNode != 0)
	{
		if (strcmp(pNode->name, data) == 0)
		{
			if (preNode == 0)
			{
				*ppNode = (*ppNode)->next;
			}
			else
			{
				preNode->next = pNode->next;
			}
			free(pNode);
			break;
		}
		preNode = pNode;
		pNode = pNode->next;
	}
	if (pNode == 0)
		printf("It's a wrong name.Please input a ture one.\n");
	return 0;
}

void findData(NodePtr list, const char* name)
{
	Node* pNode = list;
	int row = 1;
	while (pNode != 0)
	{
		if (strcmp(pNode->name, name) == 0)
		{
			printf(":%d\t%s\n", row, pNode->name);
			break;
		}
		pNode = pNode->next;
		row++;
	}
	if (pNode == 0)
	{
		printf("We can't find it,please give me a ture word and retry");
	}
	fputs("\n", stdout);

}

int enterChoice(void)
{
	int menuChoice;
	printf("\nEnter your choice\n"
		"1 - add a new account\n"
		"2 - delete an account\n"
		"3 - find and print account of your input\n"
		"4 - print list contents\n"
		"! - Press other key to stop this program\n? ");
	scanf("%d", &menuChoice);
	return menuChoice;
}
