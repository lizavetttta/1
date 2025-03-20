package javaapplication4;

public class JavaApplication4 {

    public static void main(String[] args) {
        Stack<Integer> stack = new Stack<>();
        
        stack.push(4);
        stack.push(5);
        stack.push(6);
        
        System.out.println("Вершина стека: " + stack.peek()); 
        System.out.println("Размер стека: " + stack.size()); 
        
        System.out.println("Удаляем: " + stack.pop());
        System.out.println("Теперь вершина стека: " + stack.peek()); 
        System.out.println("Теперь размер стека: " + stack.size()); 
    }

    public static class Stack<T> {
        private Node<T> top; 
        private int size; 

        // Внутренний класс для узла стека
        private static class Node<T> {
            private T data; 
            private Node<T> next; 

            public Node(T data) {
                this.data = data;
                this.next = null;
            }
        }

        // Конструктор
        public Stack() {
            this.top = null;
            this.size = 0;
        }

        // Добавление элемента на вершину стека
        public void push(T item) {
            Node<T> newNode = new Node<>(item);
            newNode.next = top; 
            top = newNode; 
            size++;
        }

        // Удаление и возврат элемента с вершины стека
        public T pop() {
            if (isEmpty()) {
                throw new RuntimeException("Стек пуст. Невозможно выполнить операцию pop.");
            }
            T item = top.data; 
            top = top.next; 
            size--;
            return item; 
        }

        // Возврат элемента с вершины стека без удаления
        public T peek() {
            if (isEmpty()) {
                throw new RuntimeException("Стек пуст. Невозможно выполнить операцию peek.");
            }
            return top.data;
        }

        // Проверка, пуст ли стек
        public boolean isEmpty() {
            return size == 0;
        }

        // Получение размера стека
        public int size() {
            return size;
        }
    }
}
