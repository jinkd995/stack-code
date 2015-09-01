using System;
using System.Collections.Generic;

class Program
{
    static void Main()
    {
	// Get the stack [See above definition of this method]
	Stack<int> stack = GetStack();

	// Pop the top element
	int pop = stack.Pop();

	// Write to the console
	Console.WriteLine("--- Element popped from top of Stack ---");
	Console.WriteLine(pop);

	// Now look at the top element
	int peek = stack.Peek();
	Console.WriteLine("--- Element now at the top ---");
	Console.WriteLine(peek);
    }
}
