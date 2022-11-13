# tree-visualiser
Visualise BSTs!

# Usage

## Serialisation
Use the following function to serialise your BST
```c
int serialise(Node* n, char* buffer, int level) {
	if (!n) return 0;
	int chars = 0;
	chars += serialise(n->left, buffer + chars, level + 1);
	chars += sprintf(buffer + chars, "%p,%d,%p,%p,%d\n", n, n->data, n->left, n->right, level);
	chars += serialise(n->right, buffer + chars, level + 1);
	return chars;
}
```

Usage:
```c
char* str = malloc(1000 * sizeof(char));
serialise(tree, str, 0); 			// pass the BST rooted at tree (eg root or root_balanced)
printf("%s", str);
free(str);
```
## Rendering
Paste the generated serial in the textbox to render the tree
![image](https://user-images.githubusercontent.com/28251020/201499666-2df3e862-bc6f-48a7-bc61-af22e81926a3.png)

> **Warning**
> Unless you have a beefy computer, trying to visualise trees with >500 nodes **will** crash your computer. The benchmark so far has been 1k nodes, courtesy of Freddie.
> ![image](https://user-images.githubusercontent.com/28251020/201521522-72081c6b-4905-4281-af3c-e9846a4fa98d.png)
