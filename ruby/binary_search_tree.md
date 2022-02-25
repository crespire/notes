# Binary Search & Binary Trees

# Binary Trees

Binary trees are a kind of data structure that we can use to represent ordered data. The rules for this data structure are very simple. A node can have, at most, 2 children. The left child is always less than the current node, and the right child is always more than the current node.

In order to construct a binary tree, we can take elements of an unordered array, store each element's contents into a node class, and then relate these notes together.

```ruby
class Node
	attr_accessor: :left, :right, :data

	def initialize(data)
		@data = data
		@left = nil
		@right = nil
	end
end
```

As an example, consider the array `[5, 7, 1, 15, 9, 2, 14, 8, 7, 3]` that would yield a tree:

![bst1](https://user-images.githubusercontent.com/36272822/155755081-8cf4f053-88a5-4355-b939-68cf9d8ec0f8.png)

Basically, starting with 5, we make nodes and insert them as children.

### Algorithm

```ruby
def build_tree(array)
    return nil if array.empty?
    return Node.new(array.first) if array.length == 1

    mid = 0 + array.length / 2
    root_node = Node.new(array[mid])
    root_node.left = build_tree(array.take(mid))
    root_node.right = build_tree(array.drop(mid + 1))

    root_node
  end
```

# Traversal

## Breath-First Traversal

## Level Order

![bst2](https://user-images.githubusercontent.com/36272822/155755099-19085bc3-1b35-4a65-9862-60332c7a53c2.png)

Image credit: mycodeschool on youtube.

We use a queue data structure to store "discovered" nodes, which helps us to complete level-order traversal. We can probably implement this using an Array. Using the queue, we only have to visit each node once, because the queue is how we store node references once we've moved past a node.

### Algorithm

```ruby
def bf_level_order(root_node)
  return if root_node.nil?
	queue = []
	queue.push(root_node)
	until queue.empty?
		current = queue.shift
		puts current # Just putting the node into console for now
		queue.push(current.left) if current.left
		queue.push(current.right) if current.right
	end

	true # Return true for traversed.
end
```

## Depth-first Traversal

Three orders that we can do our depth first traversal in.

- Pre-order (root, left, right)
- In-order (left, root, right)
- Post-order (left, right, root)

The convention with trees is usually left is lower than right, so that's where these orders come from. I imagine there may be some use cases for traveling backwards (right → left), but I can't think of any off the top of my head, so we won't cover them. The principles are the same though.

![bst3](https://user-images.githubusercontent.com/36272822/155755122-ecf31d22-1d63-4919-947c-6b6045b13c4b.png)

image credit: mycodeschool on youtube. 

Per the image above, the different depth first traversal orders would yield:

- Pre: F D B A C E J G I K
- In: A B C D E F G I J K
- Post: A C B E D I G K J F

### Algorithm
<<<<<<< Updated upstream
=======
```ruby
def df_inorder(node)
  return if node.nil? # Base case, we have empty node.

	df_inorder(node.left)
	puts node
	df_inorder(node.right)
end

def df_preorder(node)
	return if node.nil?

	puts node
	df_preorder(node.left)
	df_preorder(node.right)
end

def df_postorder(node)
	return if node.nil?

	df_postorder(node.left)
	df_postorder(node.right)
	puts node
end
```
>>>>>>> Stashed changes
