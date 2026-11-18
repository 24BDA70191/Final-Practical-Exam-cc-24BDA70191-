# Final-Practical-Exam-cc-24BDA70191-
#include <iostream>
using namespace std;

struct TreeNode {
    int val;
    TreeNode *left, *right;

    TreeNode(int x) {
        val = x;
        left = right = NULL;
    }
};

int countNodes(TreeNode* root) {
    if (root == NULL) return 0;

    return 1 + countNodes(root->left)
             + countNodes(root->right);
}

int main() {
    int n, x;
    cout << "Enter number of nodes: ";
    cin >> n;

    if (n <= 0) {
        cout << "Total nodes: 0";
        return 0;
    }

    cout << "Enter root value: ";
    cin >> x;

    TreeNode* root = new TreeNode(x);

    TreeNode* nodes[100];
    nodes[0] = root;

    for (int i = 1; i < n; i++) {
        cout << "Enter value for node " << i + 1 << ": ";
        cin >> x;
        nodes[i] = new TreeNode(x);
    }

    for (int i = 0; i < n; i++) {
        if (2*i + 1 < n)
            nodes[i]->left = nodes[2*i + 1];

        if (2*i + 2 < n)
            nodes[i]->right = nodes[2*i + 2];
    }

    cout << "Total nodes: " << countNodes(root);

    return 0;
}
