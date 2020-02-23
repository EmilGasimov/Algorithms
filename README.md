# Algorithms
class Node { 
	int data; 
	Node left_node, right_node; 

	Node(int item) 
	{ 
		data = item; 
		left_node =  null;
		right_node = null; 
	} 
} 

class Tree { 
	Node root; 

	void Morris(Node root) 
	{ 
		Node curr, prev; 

		if (root == null) 
			return; 

		curr = root; 
		while (curr != null) { 
			if (curr.left_node == null) { 
				System.out.print(curr.data + " "); 
				curr = curr.right_node; 
			} 
			else { 
				/* Find the previous (prev) of curr */
				prev = curr.left_node; 
				while (prev.right_node != null && prev.right_node != curr) 
					prev = prev.right_node; 

				/* Make curr as right child of its prev */
				if (prev.right_node == null) { 
					prev.right_node = curr; 
					curr = curr.left_node; 
				} 

				/* fix the right child of prev*/

				else { 
					prev.right_node = null; 
					System.out.print(curr.data + " "); 
					curr = curr.right_node; 
				} 

			} 

		}
	} 

	public static void main(String args[]) 
	{ 
		
		Tree tree = new Tree(); 
		tree.root = new Node(4); 
		tree.root.left_node = new Node(2); 
		tree.root.right_node = new Node(5); 
		tree.root.left_node.left_node = new Node(1); 
		tree.root.left_node.right_node = new Node(3); 

		tree.Morris(tree.root); 
	} 
} 
