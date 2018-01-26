# Data Structures

## References
 - [6 Data Structures in 6 Minutes](https://medium.com/@limichelle21/5-data-structures-in-5-minutes-7f4b34d00b8e)
 - [How do you use Queue, Stack, List, Map, and Set in Java?](https://www.quora.com/How-do-you-use-Queue-Stack-List-Map-and-Set-in-Java)
 - 用 JavaScript 學習資料結構和演算法 系列
	 - [陣列（Array）篇](https://blog.kdchang.cc/2016/06/23/javascript-data-structure-algorithm-array/)
	 - [堆疊（Stack）篇](https://blog.kdchang.cc/2016/06/24/javascript-data-structure-algorithm-stack/) *
	 - [佇列（Queue）篇](https://blog.kdchang.cc/2016/09/11/javascript-data-structure-algorithm-queue/) *
	 - [鏈結串列（Linked List）篇](https://blog.kdchang.cc/2016/09/21/javascript-data-structure-algorithm-linked-list/) *
	 - [集合（Set）篇](https://blog.kdchang.cc/2016/09/23/javascript-data-structure-algorithm-set/) *
	 - [字典（Dictionary）和雜湊表（Hash Table）篇](https://blog.kdchang.cc/2016/09/23/javascript-data-structure-algorithm-dictionary-hash-table/)
	 - [樹（Tree）篇](https://blog.kdchang.cc/2016/09/25/javascript-data-structure-algorithm-tree/) *
	 - [圖形（Graph）篇](https://blog.kdchang.cc/2016/09/26/javascript-data-structure-algorithm-graph/)
	 - [排序（Sort）與搜尋（Search）篇](https://blog.kdchang.cc/2016/09/27/javascript-data-structure-algorithm-sort-and-search/)
	 - [演算法進階補充篇](https://blog.kdchang.cc/2016/09/27/javascript-data-structure-algorithm-advance/)

## Array

![@tooto1985](https://blog.kdchang.cc/2016/06/23/javascript-data-structure-algorithm-array/ja-array-operation.jpg)

## Stack

Last In First Out (LIFO)

![tutorialspoint](https://www.tutorialspoint.com/data_structures_algorithms/images/stack_representation.jpg)


    function Stack() {
    	var items = [];
    	this.push = function(element) {
    		items.push(element);
    	}
    	this.pop = function() {
    		return items.pop();
    	}
    	this.peek = function() {
    		return items[items.length - 1];
    	}
    	this.isEmpty = function() {
    		return items.length === 0;
    	}
    	this.clear = function() {
    		items = [];
    	}
    	this.size = function() {
    		return items.length;
    	}
    	this.print = function() {
    		console.log(items.toString());
    	}
    }

    var stack = new Stack();
    stack.push('Book I');
    stack.push('Book II');
    stack.push('Book III');
    stack.push('Book IV');
    stack.pop();                   // remove BookIV

    console.log(stack.size());     // 3
    console.log(stack.peek());     // Book III
    stack.clear();                 // Clear stack
    console.log(stack.isEmpty());  // true

## Queue

First In First Out (FIFO): In **Rear**, Out **Front**

![tutorialspoint](https://www.tutorialspoint.com/data_structures_algorithms/images/queue_diagram.jpg)

![tutorialspoint](https://www.tutorialspoint.com/data_structures_algorithms/images/queue_enqueue_diagram.jpg)

    function Queue() {
    	let items = [];
    	this.enqueue = function(element) {
    		items.push(element);
    	};
    	this.dequeue = function() {
    		return items.shift();
    	};
    	this.front = function() {
    		return items[0];
    	};
    	this.isEmpty = function() {
    		return items.length === 0;
    	};
    	this.clear = function() {
    		items = [];
    	};
    	this.size = function() {
    		return items.length;
    	};
    	this.print = function() {
    		console.log(items.toString());
    	}
    }

    const queue = new Queue();

    console.log(queue.isEmpty());     // true

    queue.enqueue('Car 1');
    queue.enqueue('Car 2');
    queue.enqueue('Car 3');
    queue.enqueue('Car 4');

    console.log(queue.front());       // Car 1
    console.log(queue.size());        // 4
    queue.print();                    // Car 1,Car 2,Car 3,Car 4
    queue.dequeue();                  // remove Car 1
    console.log(queue.front());       // Car 2
    console.log(queue.size());        // 3
    queue.print();                    // Car 2,Car 3,Car 4


### Priority Queue

Set priority to each item in array.

![netmatze](https://netmatze.files.wordpress.com/2014/08/priorityqueue.png)

    function PriorityQueue() {
    	let items = [];
    	function QueueElement(element, priority) {
    		this.element = element;
    		this.priority = priority;
    	}
    	this.enqueue = function(element, priority) {
    		const queueElement = new QueueElement(element, priority);
    		if(this.isEmpty()) {
    			items.push(queueElement);
    		} else {
    			let added = false;
    			for(let i = 0; i < items.length; i++) {
    				if(queueElement.priority < items[i].priority) {
    					items.splice(i, 0, queueElement);
                      	added = true;
                      	break;
    				}
    			}
    			if(!added) {
    				items.push(queueElement);
    			}
    		}
    	}
    	this.dequeue = function() {
    		return items.shift();
    	};
    	this.front = function() {
    		return items[0];
    	};
    	this.isEmpty = function() {
    		return items.length === 0;
    	};
    	this.clear = function() {
    		items = [];
    	};
    	this.size = function() {
    		return items.length;
    	};
    	this.print = function() {
    		console.log(JSON.stringify(items));
    	}
    }

    const priorityQueue = new PriorityQueue();

    console.log(priorityQueue.isEmpty());      // true

    priorityQueue.enqueue('Tom', 2);
    priorityQueue.enqueue('Jane', 1);
    priorityQueue.enqueue('Ann', 4);
    priorityQueue.enqueue('Tina', 3);

    console.log(priorityQueue.front());        // {element: "Jane", priority: 1}
    console.log(priorityQueue.size());         // 4
    priorityQueue.print();                     // [{element: "Jane", priority: 1}, {element: "Tom", priority: 2}, ...]
    priorityQueue.dequeue();                   // remove Jane
    console.log(priorityQueue.front());        // {element: "Tom", priority: 2}
    console.log(priorityQueue.size());         // 3
    priorityQueue.print();                     // [{element: "Tom", priority: 2}, {element: "Tina", priority: 3}, ...]

## Linked List

A sequence of data structures which are connected together via links.

 - **Link** − Each Link of a linked list can store a data called an element.
 - **Next** − Each Link of a linked list contain a link to next link called Next.
 - **LinkedList** − A LinkedList contains the connection link to the first Link called First.

![tutorialspoint](https://www.tutorialspoint.com/data_structures_algorithms/images/dsa_linkedlist.jpg)

	function LinkedList() {
	  const Node = function(element) {
	    this.element = element;
	    this.next = null;
	  };

	  let length = 0;            // 存放 LinkedList 長度
	  let head = null;           // 第一個節點的指標

	  this.getHead = function() {
	    return head;
	  }

	  this.append = function(element) {
	    const node = new Node(element)
	    let current;

	    if(head === null) {
	      head = node;
	    } else {
	      current = head;
	      while(current.next) {
	          current = current.next;
	      }
	      current.next = node;
	    }
	    length++;
	  };

	  this.insert = function(position, element) {
	    if(position >= 0 && position <= length) {
	      let node = new Node(element);
	      let current = head;
	      let previous;
	      let index = 0;

	      if(position === 0) {
	        node.next = current;
	        head = node;
	      } else {
	        while(index++ < position) {
	            previous = current;
	            current = current.next;
	        }
	        node.next = current;
	        previous.next = node;
	      }
	      length++;
	      return true;
	    } else {
	      return false;
	    }
	  };

	  this.remove = function(element) {
	    let index = this.indexOf(element);
	    return this.removeAt(index);
	  };

	  this.removeAt = function(position) {
	    if(position > -1 && position < length) {
	      let current = head;
	      let previous;
	      let index = 0;
	      if(position === 0) {
	        head = current.next;
	      } else {
	        while(index++ < position) {
	          previous = current;
	          current = current.next;
	        }
	        previous.next = current.next;
	      }
	      length--;
	      return current.element;
	    } else {
	      return null;
	    }
	  };

	  this.indexOf = function(element) {
	    var current = head;
	    var index = -1;

	    while(current) {
	      if(element === current.element) {
	          return index;
	      }
	      index++;
	      current = current.next;
	    }
	    return -1;
	  };

	  this.isEmpty = function() {
	    return length === 0;
	  };

	  this.size = function() {
	      return length;
	  };

	  this.toString = function() {
	    let current = head;
	    let string = '';
	    while(current) {
	      string += current.element;
	      current = current.next;
	    }
	    return string;
	  };

	  this.print = function() {
	    console.log(this.toString());
	  };
	};

	const linkdeList = new LinkedList();

	console.log(linkdeList.isEmpty());     // true

	linkedList.append('A');
	linkedList.append('B');
	linkedList.append('C');
	linkedList.append('D');
	linkedList.print();                    // ABCD
	linkedList.insert(2, 'X');             // add X after node2(B)
	linkedList.print();                    // ABbCD
	linkedList.remove('B');                // remove B
	console.log(linkedList.size());        // 4
	linkedList.removeAt(0);                // remove node0 (A)
	linkedList.print();                    // XCD
	console.log(linkedList.indexOf('X'));  // -1
	console.log(linkedList.indexOf('D'));  // 1
	console.log(linkedList.getHead());     // { element: "X", next: { element: "C", next: { ... } } }

### Types

 - Singly Linked List
![studytonight](https://www.studytonight.com/data-structures/images/linked-list-linear.png)
 - Doubly Linked List
![studytonight](https://www.studytonight.com/data-structures/images/linked-list-double.png)
 - Circular Linked List
![studytonight](https://www.studytonight.com/data-structures/images/linked-list-circular.png)

## Set

![wikistack](http://wikistack.com/wp-content/uploads/2015/04/disjsds.jpeg)


	function Set() {
	  var items = {};

	  this.add = function(value) {
	    if(!this.has(value)) {
	      items[value] = value;
	      return true;
	    }
	    return false;
	  };

	  this.remove = function(value) {
	    if(this.has(value)) {
	      delete items[value];
	      return true;
	    }
	    return false;
	  };

	  this.has = function(value) {
	    return items.hasOwnProperty(value);
	  };

	  this.clear = function() {
	    items = {};
	  };

	  this.size = function() {
	    let count = 0;
	    for(let key in items) {
	      ++count;
	    }
	    return count;
	  };

	  this.value = function() {
	    let keys = [];
	    for(let key in items) {
	      keys.push(key);
	    }
	    return keys;
	  };

	  this.union = function(otherSet) {
	    let unionSet = new Set();
	    let value = this.value();
	    for(var i = 0; i < value.length; i++) {
	      unionSet.add(value[i]);
	    }
	    value = otherSet.value();
	    for(var j = 0; j < value.length; j++) {
	      unionSet.add(value[j]);
	    }
	    return unionSet;
	  };

	  this.intersection = function(otherSet) {
		let intersectionSet = new Set();
		let value = this.value();
		for(var i = 0; i < value.length; i++) {
			if(otherSet.has(value[i])) {
				intersectionSet.add(value[i]);
			}
		}
		return intersectionSet;
	  };

	  this.difference = function(otherSet) {
	    let differenceSet = new Set();
	    let value = this.value();
	    for(var i = 0; i < value.length; i++) {
	      if(!otherSet.has(value[i])) {
	        differenceSet.add(value[i]);
	      }
	    }
	    return differenceSet;
	  }

	  this.isSub = function(otherSet) {
	    if(this.size() > otherSet.size()) {
	      return false;
	    } else {
	      let value = this.value();
	      for(var i = 0; i < value.length; i++) {
	        if(!otherSet.has(value[i])) {
	          return false;
	        }
	      }
	      return true;
	    }
	  };
	}

	const set = new Set();

	set.add(12);                                         // add 12
	console.log(set.value());                            // ['12']
	console.log(set.has(12));                            // true
	console.log(set.size());                             // 1
	set.add(15);                                         // add 15
	set.remove(12);                                      // remove 12
	console.log(set.has(12));                            // false
	console.log(set.value());                            // ['15']

	let setA = new Set();
	setA.add('A');
	setA.add('B');
	setA.add('C');
	setA.add('D');
	console.log(setA.value());                           // ["A", "B", "C", "D"]

	let setB = new Set();
	setB.add('A');
	setB.add('C');
	setB.add('E');
	setB.add('F');
	console.log(setB.value());                           // ["A", "C", "E", "F"]

	let setC = new Set();
	setC.add('A');
	setC.add('B');

	const unionSet = setA.union(setB);
	console.log(unionSet.value());                       // ["A", "B", "C", "D", "E", "F"]

	const intersectionSet = setA.intersection(setB);
	console.log(intersectionSet.value());                // ["A", "C"]

	const differenceSet = setA.difference(setB);
	console.log(differenceSet.value());                  // ["A", "C"]

	console.log(setB.isSub(setA));                       // false
	console.log(setC.isSub(setA));                       // true


## Tree

 - **inorder**: left -> root -> right (A -> B -> C)
 - **preorder**: root -> left -> right (B -> A -> C)
 - **postorder**: left -> right -> root (A -> C -> B)

![medium](https://cdn-images-1.medium.com/max/800/1*87h2uhCJ5qztBNwfck2b6g.jpeg)

	function BinarySearchTree() {
	  const Node = function(key) {
	    this.key = key;
	    this.left = null;
	    this.right = null;
	  };

	  let root = null;

	  this.insert = function(key) {
	    let newNode = new Node(key);

	    if(root === null) {
	      root = newNode;
	    } else {
	      insertNode(root, newNode);
	    }
	  };
	  const insertNode = function(node, newNode) {
	    if(newNode.key < node.key) {
	      if(node.left === null) {
	        node.left = newNode;
	      } else {
	        insertNode(node.left, newNode);
	      }
	    } else {
	      if(node.right === null) {
	        node.right = newNode;
	      } else {
	        insertNode(node.right, newNode);
	      }
	    }
	  };

	  this.inOrderTraverse = function(callback) {
	    inOrderTraverseNode(root, callback);
	  };
	  const inOrderTraverseNode = function(node, callback) {
	    if(node !== null) {
	      inOrderTraverseNode(node.left, callback);
	      callback(node.key);
	      inOrderTraverseNode(node.right, callback);
	    }
	  }

	  this.preOrderTraverse = function(callback) {
	    preOrderTraverseNode(root, callback);
	  };
	  const preOrderTraverseNode = function(node, callback) {
	    if(node !== null) {
	      callback(node.key);
	      preOrderTraverseNode(node.left, callback);
	      preOrderTraverseNode(node.right, callback);
	    }
	  };

	  this.postOrderTraverse = function(callback) {
	    postOrderTraverseNode(root, callback);
	  };
	  const postOrderTraverseNode = function(node, callback) {
	    if(node !== null) {
	      postOrderTraverseNode(node.left, callback);
	      postOrderTraverseNode(node.right, callback);
	      callback(node.key);
	    }
	  };

	  this.search = function(key) {
	    return searchNode(root, key);
	  };
	  const searchNode = function(node, key) {
	    if(node === null) {
	      return false;
	    }
	    if (key === node.key) {
	      return true;
	    }
	    if (key < node.key) {
	      return searchNode(node.left, key);
	    } else if (key > node.key) {
	      return searchNode(node.right, key);
	    }
	  };

	  this.min = function() {
	    return minNode(root);
	  };
	  const minNode = function(node) {
	    if(node) {
	      while(node && node.left !== null) {
	        node = node.left;
	      }
	      return node.key;
	    }
	    return null;
	  };

	  this.max = function() {
	    return maxNode(root);
	  };
	  const maxNode = function(node) {
	    if(node) {
	      while(node && node.right !== null) {
	        node = node.right;
	      }
	      return node.key;
	    }
	    return null;
	  };

	  this.remove = function(key) {
	    if(this.search(key)) {
	      return removeAt(root, key);
	    } else {
	      console.log('No such node.');
	    }
	  };
	  const removeAt = function(node, key) {
	    if(node === null) {
	      node.left = removeAt(node.left, key);
	      return node;
	    } else if(key > node.key) {
	      node.right = removeAt(node.right, key);
	    } else {
	      if(node.left === null) {
	        node = node.right;
	        return node;
	      }
	      if(node.left === null) {
	        node = node.right;
	        return node;
	      } else if(node.right === null) {
	        node = node.left;
	        return node;
	      }
	      const aux = this.search(node.right);
	      node.key = removeAt(node.right, aux.key);
	      return node;
	    }
	  };
	};

	function printNode(value) {
		console.log(value);
	}

	let tree = new BinarySearchTree();
	tree.insert(35);
	tree.insert(22);
	tree.insert(7);
	tree.insert(2);
	tree.insert(4);
	tree.insert(5);
	tree.insert(32);
	tree.insert(40);
	tree.inOrderTraverse(printNode);            // 2 4 5 7 22 32 35 40
	tree.preOrderTraverse(printNode);           // 35 22 7 2 4 5 32 40
	tree.postOrderTraverse(printNode);          // 5 4 2 7 32 22 40 35

	// tree.remove(5);
	// tree.inOrderTraverse(printNode);            // 2 4 5 7 22 32 35 40
	tree.remove(1);
	tree.inOrderTraverse(printNode);            // 2 4 5 7 22 32 35 40

	console.log(tree.min());                    // 2
	console.log(tree.max());                    // 40
	console.log(tree.search(8));                // false
	console.log(tree.search(22));               // true
