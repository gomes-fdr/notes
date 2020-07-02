---
title: "Notas sobre C++ e o Framework Qt"
date: 2020-06-05
slug: "notas-sobre-cpp-e-o-framework-qt"
tags: ["cpp"]
draft: false
---

## Uso de notação húngara

Bastante usada por programadores vindos do Pascal ou Fortram, tenta, através de notação inferir de que tipo ou contexto está tratando.

	/*
		g_nWheels : member of a global namespace, integer
		m_nWheels : member of a structure/class, integer
		m_wheels, _wheels : member of a structure/class
		s_wheels : static member of a class
		c_wheels : static member of a function
	*/


## Sobre passagem por referência e por valor

Algumas referências para entender como funciona o uso de referências ou valores.

	// C++ program to demonstrate differences between pointer and reference. 
	#include <iostream> 
	using namespace std; 

	struct demo { 
		int a;
	}; 

	int main() { 
	​	int x = 5; 
	​	int y = 6; 
	​	demo d; 
	​	int *p; 
	​	p = &x; 
	​	p = &y;					// 1. Pointer reintialization allowed 
	​	int &r = x; 
	​	// &r = y;				// 1. Compile Error 
	​	r = y;					// 1. x value becomes 6 
	​	p = NULL; 
	​	// &r = NULL;			 	// 2. Compile Error 
	​	p++;					// 3. Points to next memory location 
	​	r++;					// 3. x values becomes 7 

	​	cout << &p << " " << &x << endl; 	// 4. Different address 
	​	cout << &r << " " << &x << endl; 	// 4. Same address 

	​	demo *q = &d; 
	​	demo &qq = d; 
	​	q->a = 8; 

	​	// q.a = 8;				 // 5. Compile Error 
	​	qq.a = 8; 
	​	// qq->a = 8;			 	 // 5. Compile Error 

	​	cout << p << endl;	 		 // 6. Prints the address 
	​	cout << r << endl;	 		 // 6. Print the value of x
	​	return 0; 
	} 

[Referência](https://www.geeksforgeeks.org/passing-by-pointer-vs-passing-by-reference-in-c/)

## Sobre o uso de const values

Outra figurinha carimbada, o uso de `const` - aqui algumas aplicações de uso.

	#include <iostream>

	// x is a const reference to the argument passed in, not a copy
	void printIt(const int &x) {
	​    std::cout << x;
	}

	int main() {
	​    int a = 1;
	​    printIt(a); 	// non-const l-value

	​    const int b = 2;
	​    printIt(b); 	// const l-value
	​    printIt(3); 	// literal r-value
	​    printIt(2+b); 	// expression r-value

	​    return 0;
	}

[Referência](https://www.learncpp.com/cpp-tutorial/6-11a-references-and-const/)

**Rule:**  Pass non-pointer, non-fundamental data type variables (such as structs) by (const) reference.

## Sobre auto_ptr

Essa feature permite o uso de tipo por inferição, ou seja, o tipo da variável é definido do lado direito da igualdade(sinal de atribuição).


	// C++ program to demonstrate working of auto and type inference 
	#include <bits/stdc++.h> 

	using namespace std; 

	int main() { 
	​	auto x = 4; 
	​	auto y = 3.37; 
	​	auto ptr = &x; 

	​	cout << typeid(x).name() << endl 
 	​	     << typeid(y).name() << endl 
	​	     << typeid(ptr).name() << endl; 

	​	return 0; 
	}

[Referência](https://www.geeksforgeeks.org/type-inference-in-c-auto-and-decltype/)

## Uso de iteradores

Um recurso muito bacana da linguagem, permite subir o nível da conversa quando se fala de *navegar* em coleções.


	#include <iostream>
	#include <vector>

	int main() {
	​    std::vector<int> v = {0, 1, 2, 3, 4, 5};
	 
	​    for (const int& i : v) // access by const reference
	​        std::cout << i << ' ';
	​    std::cout << '\n';

	​    for (auto i : v) // access by value, the type of i is int
	​        std::cout << i << ' ';
	​    std::cout << '\n';

	​    for (auto&& i : v) // access by forwarding reference, the type of i is int&
	​        std::cout << i << ' ';
	​    std::cout << '\n';

	​    const auto& cv = v;
	​    for (auto&& i : cv) // access by f-d reference, the type of i is const int&
	​        std::cout << i << ' ';
	​    std::cout << '\n';

	​    for (int n : {0, 1, 2, 3, 4, 5}) // the initializer may be a braced-init-list
	​        std::cout << n << ' ';
	​    std::cout << '\n';
	 
	​    int a[] = {0, 1, 2, 3, 4, 5};
	​    for (int n : a) // the initializer may be an array
	​        std::cout << n << ' ';
	​    std::cout << '\n';

	​    for (int n : a)
	​        std::cout << 1 << ' '; // the loop variable need not be used
	​    std::cout << '\n';
	}

[Referência](https://en.cppreference.com/w/cpp/language/range-for)

## Sobre lambda functions

Ou funções anônimas, mais um recurso interessante da linguagem


	// C++ program to demonstrate lambda expression in C++ 
	#include <bits/stdc++.h> 

	using namespace std; 

	int main() { 
	​	vector<int> v1 = {3, 1, 7, 9}; 
	​	vector<int> v2 = {10, 2, 7, 16, 9}; 

	​	// access v1 and v2 by reference 
	​	auto pushinto = [&] (int m) {
	​		v1.push_back(m); 
	​		v2.push_back(m); 
	​	}; 

	​	// it pushes 20 in both v1 and v2 
	​	pushinto(20); 

	​	// access v1 by copy 
	​	[v1]() { 
	​		for (auto p = v1.begin(); p != v1.end(); p++) { 
	​			cout << *p << " ";
	​		} 
	​	}; 

	​	int N = 5; 
	​	// below snippet find first number greater than N 
	​	// [N] denotes, can access only N by value 
	​	vector<int>:: iterator p = find_if(v1.begin(), v1.end(), [N](int i) { 
	​		return i > N;
	​	}); 

	​	cout << "First number greater than 5 is : " << *p << endl; 

	​	// function to count numbers greater than or equal to N 
	​	// [=] denotes, can access all variable 
	​	int count_N = count_if(v1.begin(), v1.end(), [=](int a) {
	​		return (a >= N);
	​	}); 

	​	cout << "The number of elements greater than or equal to 5 is : "
	​	     << count_N << endl; 
	} 

[Referência 1](https://www.geeksforgeeks.org/lambda-expression-in-c/)
[Referência 2](https://docs.microsoft.com/pt-br/cpp/cpp/lambda-expressions-in-cpp?view=vs-2019)

## Sobre uso de excessões


	#include <iostream>

	using namespace std;

	double division(int a, int b) {
	   if( b == 0 ) {
	​      throw "Division by zero condition!";
	   }

	   return (a/b);
	}

	int main () {
	   int x = 50;
	   int y = 0;
	   double z = 0;

	   try {
	​      z = division(x, y);
	​      cout << z << endl;

	   } catch (const char* msg) {
	​     cerr << msg << endl;
	   }

	   return 0;
	}

[Referência](https://www.tutorialspoint.com/cplusplus/cpp_exceptions_handling.htm)

## Criando excessões


	#include <iostream>
	#include <exception>

	using namespace std;

	struct MyException : public exception {
	   const char * what () const throw () {
	​      return "C++ Exception";
	   }
	};

	int main() {
	   try {
	​      throw MyException();
	   } catch(MyException& e) {
	​      std::cout << "MyException caught" << std::endl;
	​      std::cout << e.what() << std::endl;
	   } catch(std::exception& e) {
	​      //Other errors
	   }
	}

## Referência da linguagem

  * [Geeks for geeks](https://www.geeksforgeeks.org/c-plus-plus/)
  * [CPP Reference](https://en.cppreference.com/w/cpp/language)
  * [CPP crash course](https://github.com/rougier/cpp-crash-course)
  * [Notação Hungara](https://en.wikipedia.org/wiki/Hungarian_notation)
  * [Documentação oficial](https://doc.qt.io/)
  * [Clean Qt](https://www.cleanqt.io/home)
