# Range-Sum-of-BST
Given the root node of a binary search tree and two integers low and high, return the sum of values of all nodes with a value in the inclusive range [low, high].   

class TreeNode:
    def __init__(self, val=0, left=None, right=None):
        self.val = val
        self.left = left
        self.right = right

class Solution:
    def rangeSumBST(self, root, low, high):
        if not root:
            return 0

       
        current_val = 0
        if low <= root.val <= high:
            current_val = root.val

        left_sum = self.rangeSumBST(root.left, low, high)
        right_sum = self.rangeSumBST(root.right, low, high)

        return current_val + left_sum + right_sum


root1 = TreeNode(10)
root1.left = TreeNode(5, TreeNode(3), TreeNode(7))
root1.right = TreeNode(15, None, TreeNode(18))


solution = Solution()
print(solution.rangeSumBST(root1, 7, 15))  # Output: 32


root2 = TreeNode(10)
root2.left = TreeNode(5, TreeNode(3, TreeNode(1), None), TreeNode(7, TreeNode(6)))
root2.right = TreeNode(15, TreeNode(13), TreeNode(18))


print(solution.rangeSumBST(root2, 6, 10))  # Output: 23
