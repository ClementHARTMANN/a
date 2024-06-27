
### 1. Méthodes virtuelles

```cpp
#include <iostream>

class Base {
public:
    virtual void display() const {
        std::cout << "Base display" << std::endl;
    }
};

class Derived : public Base {
public:
    void display() const override {
        std::cout << "Derived display" << std::endl;
    }
};

int main() {
    Base* b = new Derived();
    b->display(); // Output: Derived display
    delete b;
    return 0;
}
```

### 2. Surcharge (Overloading)

```cpp
#include <iostream>

class Example {
public:
    void display(int a) {
        std::cout << "Integer: " << a << std::endl;
    }

    void display(double a) {
        std::cout << "Double: " << a << std::endl;
    }
};

int main() {
    Example ex;
    ex.display(5);     // Output: Integer: 5
    ex.display(5.5);   // Output: Double: 5.5
    return 0;
}
```

### 3. Masquage (Hiding)

```cpp
#include <iostream>

class Base {
public:
    void display() {
        std::cout << "Base display" << std::endl;
    }
};

class Derived : public Base {
public:
    void display() {
        std::cout << "Derived display" << std::endl;
    }
};

int main() {
    Derived d;
    d.display(); // Output: Derived display
    d.Base::display(); // Output: Base display
    return 0;
}
```

### 4. Programmation modulaire et compilation séparée

**Fichier `main.cpp`**

```cpp
#include <iostream>
#include "module.h"

int main() {
    greet();
    return 0;
}
```

**Fichier `module.h`**

```cpp
#ifndef MODULE_H
#define MODULE_H

void greet();

#endif // MODULE_H
```

**Fichier `module.cpp`**

```cpp
#include <iostream>
#include "module.h"

void greet() {
    std::cout << "Hello, Modular World!" << std::endl;
}
```

### 5. POO (Programmation Orientée Objet)

```cpp
#include <iostream>

class Animal {
public:
    void speak() {
        std::cout << "Animal speaks" << std::endl;
    }
};

int main() {
    Animal a;
    a.speak(); // Output: Animal speaks
    return 0;
}
```

### 6. Surcharge de constructeurs

```cpp
#include <iostream>

class Point {
public:
    Point() : x(0), y(0) {}
    Point(int x, int y) : x(x), y(y) {}

    void display() const {
        std::cout << "Point(" << x << ", " << y << ")" << std::endl;
    }

private:
    int x, y;
};

int main() {
    Point p1;
    Point p2(3, 4);
    p1.display(); // Output: Point(0, 0)
    p2.display(); // Output: Point(3, 4)
    return 0;
}
```

### 7. Méthodes non statiques

```cpp
#include <iostream>

class Example {
public:
    void display() {
        std::cout << "Non-static method" << std::endl;
    }
};

int main() {
    Example ex;
    ex.display(); // Output: Non-static method
    return 0;
}
```

### 8. Héritage et héritage multiple

```cpp
#include <iostream>

class A {
public:
    void displayA() {
        std::cout << "Class A" << std::endl;
    }
};

class B {
public:
    void displayB() {
        std::cout << "Class B" << std::endl;
    }
};

class C : public A, public B {
public:
    void displayC() {
        std::cout << "Class C" << std::endl;
    }
};

int main() {
    C c;
    c.displayA(); // Output: Class A
    c.displayB(); // Output: Class B
    c.displayC(); // Output: Class C
    return 0;
}
```

### 9. Tableaux

```cpp
#include <iostream>

int main() {
    int arr[5] = {1, 2, 3, 4, 5};
    for(int i = 0; i < 5; ++i) {
        std::cout << arr[i] << " ";
    }
    // Output: 1 2 3 4 5
    return 0;
}
```

### 10. Listes chaînées

```cpp
#include <iostream>

struct Node {
    int data;
    Node* next;
};

void printList(Node* n) {
    while (n != nullptr) {
        std::cout << n->data << " ";
        n = n->next;
    }
}

int main() {
    Node* head = new Node();
    Node* second = new Node();
    Node* third = new Node();

    head->data = 1;
    head->next = second;
    second->data = 2;
    second->next = third;
    third->data = 3;
    third->next = nullptr;

    printList(head); // Output: 1 2 3

    // Libération de la mémoire
    delete head;
    delete second;
    delete third;

    return 0;
}
```

### 11. Pointeurs, paramètres par valeur et par adresse

```cpp
#include <iostream>

void swap(int* a, int* b) {
    int temp = *a;
    *a = *b;
    *b = temp;
}

int main() {
    int x = 10, y = 20;
    swap(&x, &y);
    std::cout << "x: " << x << ", y: " << y << std::endl; // Output: x: 20, y: 10
    return 0;
}
```

### 12. Structures

```cpp
#include <iostream>

struct Point {
    int x;
    int y;
};

int main() {
    Point p1 = {10, 20};
    std::cout << "Point(" << p1.x << ", " << p1.y << ")" << std::endl; // Output: Point(10, 20)
    return 0;
}
```

### 13. Fonctions récursives

```cpp
#include <iostream>

int factorial(int n) {
    if (n <= 1) {
        return 1;
    }
    return n * factorial(n - 1);
}

int main() {
    int num = 5;
    std::cout << "Factorial of " << num << " is " << factorial(num) << std::endl; // Output: Factorial of 5 is 120
    return 0;
}
```

```cpp
#include <iostream>
#include <string>
#include <vector>

// Structures basiques
struct Point {
    int x;
    int y;
};

// Classe de base avec méthodes virtuelles
class Book {
public:
    Book(const std::string& title, const std::string& author)
        : title(title), author(author) {}

    virtual ~Book() {}

    virtual void displayInfo() const {
        std::cout << "Title: " << title << ", Author: " << author << std::endl;
    }

protected:
    std::string title;
    std::string author;
};

// Classe dérivée avec surcharge de méthodes
class EBook : public Book {
public:
    EBook(const std::string& title, const std::string& author, const std::string& format)
        : Book(title, author), format(format) {}

    void displayInfo() const override {
        std::cout << "Title: " << title << ", Author: " << author << ", Format: " << format << std::endl;
    }

private:
    std::string format;
};

// Héritage multiple
class PrintedBook : public Book {
public:
    PrintedBook(const std::string& title, const std::string& author, int pages)
        : Book(title, author), pages(pages) {}

    void displayInfo() const override {
        std::cout << "Title: " << title << ", Author: " << author << ", Pages: " << pages << std::endl;
    }

private:
    int pages;
};

// Listes chaînées
struct Node {
    Book* book;
    Node* next;
};

// Classe de gestion de bibliothèque
class Library {
public:
    Library() : head(nullptr) {}

    ~Library() {
        Node* current = head;
        while (current != nullptr) {
            Node* next = current->next;
            delete current->book;
            delete current;
            current = next;
        }
    }

    void addBook(Book* book) {
        Node* newNode = new Node();
        newNode->book = book;
        newNode->next = head;
        head = newNode;
    }

    void displayBooks() const {
        Node* current = head;
        while (current != nullptr) {
            current->book->displayInfo();
            current = current->next;
        }
    }

private:
    Node* head;
};

// Fonction récursive
int factorial(int n) {
    if (n <= 1) {
        return 1;
    }
    return n * factorial(n - 1);
}

// Fonction avec pointeurs et paramètres par référence
void swap(int* a, int* b) {
    int temp = *a;
    *a = *b;
    *b = temp;
}

int main() {
    Library library;

    Book* book1 = new Book("1984", "George Orwell");
    Book* ebook = new EBook("Digital Fortress", "Dan Brown", "PDF");
    Book* pbook = new PrintedBook("The Hobbit", "J.R.R. Tolkien", 310);

    library.addBook(book1);
    library.addBook(ebook);
    library.addBook(pbook);

    std::cout << "Library Books:" << std::endl;
    library.displayBooks();

    // Utilisation des tableaux
    int arr[] = {1, 2, 3, 4, 5};
    std::cout << "\nArray Elements: ";
    for (int i = 0; i < 5; ++i) {
        std::cout << arr[i] << " ";
    }
    std::cout << std::endl;

    // Utilisation des listes chaînées
    Node* head = new Node();
    Node* second = new Node();
    Node* third = new Node();

    head->book = new Book("Head Book", "Head Author");
    head->next = second;

    second->book = new Book("Second Book", "Second Author");
    second->next = third;

    third->book = new Book("Third Book", "Third Author");
    third->next = nullptr;

    std::cout << "\nLinked List: ";
    Node* current = head;
    while (current != nullptr) {
        current->book->displayInfo();
        current = current->next;
    }

    // Libération de la mémoire des livres dans la liste chaînée
    delete head->book;
    delete second->book;
    delete third->book;
    delete head;
    delete second;
    delete third;

    // Utilisation de structures
    Point p1 = {10, 20};
    std::cout << "\nPoint(" << p1.x << ", " << p1.y << ")" << std::endl;

    // Utilisation de fonctions récursives
    int num = 5;
    std::cout << "Factorial of " << num << " is " << factorial(num) << std::endl;

    // Utilisation de pointeurs et paramètres par référence
    int x = 10, y = 20;
    swap(&x, &y);
    std::cout << "x: " << x << ", y: " << y << std::endl; // Output: x: 20, y: 10

    return 0;
}
```
