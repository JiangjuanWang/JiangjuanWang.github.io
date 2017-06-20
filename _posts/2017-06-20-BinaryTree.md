---
layout: post
title: BinaryTree
---
###链表相关的算法

1.节点的定义
>包括节点的的值，左孩子的指针，右孩子的指针<br>
><br>

```java
class Node<T>{
	private T data;
	private Node<T> leftchild;
	private Node<T> rightchild;
	Node(){}
	Node(T data,Node<T> leftchild,Node<T> rightchild){
		this.data=data;
		this.leftchild=leftchild;
		this.rightchild=rightchild;
	}
	public Node(T data) {
		this.data=data;
	}
	public T getData(){
		return data;
	}
	public void setData(T data){
		this.data=data;
	}
	public Node<T> getLeftChild(){
		return leftchild;
	}
	public void setLeftChild(Node<T> leftchild){
		this.leftchild=leftchild;
	}
	public Node<T> getRightChild(){
		return rightchild;
	}
	public void setRightChild(Node<T> rightchild){
		this.rightchild=rightchild;
	}
}
```

2.先序递归建立儿二叉树（从键盘输入）
>从键盘输入待构建的二叉树的先序遍历，用“#”表示空节点<br>

```java
	public void buildBinaryTree(){
		Scanner scn=null;
		try{
			scn=new Scanner(System.in);
		}catch(Exception e){
			e.printStackTrace();
		}
		this.root=buildBinaryTree(root,scn);
	}
	public Node<T> buildBinaryTree(Node<T> node,Scanner scn){
		String s=scn.next();
		if(s.trim().equals("#")){
			return null;
		}
		else{
			node=new Node<T>((T)s);
			node.setLeftChild(buildBinaryTree(node.getLeftChild(),scn));
			node.setRightChild(buildBinaryTree(node.getRightChild(),scn));
		}
		return node;
	}
```

3.二叉树的遍历
>先序递归遍历<br>

```java
public void preOrder(){
	preOrder(root);
}
public void preOrder(Node<T> node){
	if(node!=null){
		System.out.print(node.getData());
		preOrder(node.getLeftChild());
		preOrder(node.getRightChild());
	}
}
```

>先序非递归遍历<br>

```java
	public void nrPreOrder(){
		Stack<Node> stack=new Stack<Node>();
		Node<T> node=root;
		while(node!=null || !stack.isEmpty()){
			while(node!=null){
				System.out.print(node.getData());
				stack.push(node);
				node=node.getLeftChild();
			}
			node=stack.pop();
			node=node.getRightChild();
		}
	}
```

>中序递归遍历<br>

```java
public void inOrder(){
	inOrder(root);
}
public void inOrder(Node<T> node){
	if(node!=null){
		inOrder(node.getLeftChild());
		System.out.print(node.getData());
		inOrder(node.getRightChild());
	}
}
```

>中序非递归遍历<br>

```java
	public void nrInOrder(){
		Stack<Node<T>> stack=new Stack<Node<T>>();
		Node<T> node=root;
		while(node!=null || !stack.isEmpty()){
			while(node!=null){
				stack.push(node);
				node=node.getLeftChild();
			}
			node=stack.pop();
			System.out.print(node.getData());
			node=node.getRightChild();
		}
	}
```

>后序递归遍历<br>

```java
public void postOrder(){
	postOrder(root);
}
public void postOrder(Node<T> node){
	if(node!=null){
		postOrder(node.getLeftChild());
		postOrder(node.getRightChild());
		System.out.print(node.getData());
	}
}
```

>后序非递归遍历<br>

```java
	public void levelOrder(){
		Queue<Node<T>> queue= new LinkedList<Node<T>>();
		Node<T> node=root;
		queue.add(node);
		while(!queue.isEmpty()){
			node=queue.poll();
			if(node!=null){
				System.out.print(node.getData());
				queue.add(node.getLeftChild());
				queue.add(node.getRightChild());
			}
		}
	}
```

>层次遍历<br>
```java
```

4.节点的删除
