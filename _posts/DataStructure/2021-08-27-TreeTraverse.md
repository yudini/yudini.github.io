---
layout: post
title:  "[자료구조] 이진트리 순회 "
date: 2021-08-27
author: yudini
categories: DataStructure Study
comments: true
tags: Tree TreeTraverse Traverse DataStructure 
---

## 이진트리 순회 방법에는 총 3가지가 있다.
### 전위순회(Preorder traverse): *Root - Left -Right*
### 중위순회(Inorder traverse): *Left - Root -Right*
### 후위 순회(PostOrder traverse): *Left - Right - Root*

<hr>


![Complete Binary Tree](/assets/images/CompleteTree.jpg)
<br>
<br>

<h4 style="color:blue"> 전위순회: A - B - D - H - I - E - C - F - G </h4>

<h4 style ="color:blue">중위순회: H - D - I - B - E - A - F - C - G</h4>

<h4 style ="color:blue">후위순회: H - I - D - E - B - F - G - C - A</h4>


<br>
<br>
linked list를 사용해서 스택 구현

~~~c++
#include <stdio.h>
#include <stdlib.h>

int number=15;


typedef struct node{
    int data;
    struct node *left;
    struct node *right;
}node;                                                                                         

//전위 순회(Root - Left - Right)
void preorder(node *ptr){
    if(ptr){
        printf("%d ",ptr->data);
        preorder(ptr->left);
        preorder(ptr->right);
    }
}

//중위 순회 (Left - Root -Right)
void inorder(node *ptr){
    if(ptr){
       inorder(ptr->left);
       printf("%d ",ptr->data);
       inorder(ptr->right);
    }
}

//후위 순회  (Left - Right - Root)
void postorder(node *ptr){
    if(ptr){
        postorder(ptr->left);
        postorder(ptr->right);
        printf("%d ",ptr->data);
    }
}

int main(){
    int i;
    node nodes[number+1];

    for(i=1;i<=number;i++){
        nodes[i].data=i;
        nodes[i].left=NULL;
        nodes[i].right=NULL;
    }
    for(i=1;i<=number;i++){
        if(i%2==0)
            nodes[i/2].left=&nodes[i];
        else
            nodes[i/2].right=&nodes[i];
    }

    preorder(&nodes[1]);
    printf("\n");
    inorder(&nodes[1]);
    printf("\n");
    postorder(&nodes[1]);

}
 



~~~

<hr>


<h4>&#8251;오류가 있다면 댓글로 알려주세요!</h4>
