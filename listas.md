# Ejercicios Linked Lists


### Funcion Constructora del nodo
```
function Node(val) {
  this.val = val;
  this.next = null;
}
```
### Funcion Constructora del Linked Lists
```
function LinkedList() {
  this.size = 0;
  this.head = null;
  this.tail = null;
}
```

## Funcion add O(1)
```
LinkedList.prototype.add = function(val) {
  let nodo = new Node(val);
  if (!this.head) {
    this.head = nodo;
    this.tail = nodo;
    this.size++;
  } else {
    this.tail.next = nodo;
    this.tail = nodo;
    this.size++;
  }
  return nodo;
}
```

## Funcion addAt O(n)

```
LinkedList.prototype.addAt = function(val, pos) {
  let nodo = new Node(val);
  if (!this.head) {
    this.head = nodo;
    this.tail = nodo;
    this.size++;
    return nodo;
  }
  if (pos === 0) {
    let aux = this.head;
    this.head = nodo;
    this.head.nex = aux
    this.size++;
    return nodo;
  }
  const previo = this.valueAt(pos - 1);
  let newNode = new Node(val);
  newNode.next = previo.next;
  previo.next = newNode;
  this.size++;
  return this.head
}
```

## Funcion valueAt O(n)

```
LinkedList.prototype.valueAt = function(pos) {
  let cont = 0;
  let nodo = this.head
  while (nodo) {
    if (cont === pos) {
      return nodo;
    }
    cont++;
    nodo = nodo.next;
  }
  return null;
}
```

## Funcion length O(1)

```
LinkedList.prototype.length = function() {
  return this.size;
}
```

## Funcion remove O(n)

```
LinkedList.prototype.remove = function(pos) {
  if (!this.head) {
    this.head = new Node(val);
    return;
  }
  if (pos === 0) {
    this.head = this.head.next;
    this.size--;
    return;
  }
  const previous = this.valueAt(pos - 1);

  if (!previous || !previous.next) {
    this.size--;
    return;
  }

  previous.next = previous.next.next;
  this.size--;
  return this.head
}
```
