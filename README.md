#include <string.h>
#include <stdbool.h>
bool verifyRegistration(char registration[]) 
{
 if (strlen(registration) != 10) 
 {
 return false;
 }
 for (int i = 0; i < 2; i++) 
 {
 if (!isalpha(registration[i])) 
 {
 return false;
 }
 }
 // Check if the next two characters are numbers (e.g., "09" for a specific district)
 for (int i = 2; i < 4; i++) 
 {
 if (!isdigit(registration[i])) 
 {
 return false;
 }
 }
 for (int i = 4; i < 6; i++) 
 {
 if (!isalpha(registration[i])) 
 {
 return false;
 }
 }
 for (int i = 6; i < 10; i++) 
 {
 if (!isdigit(registration[i])) 
 {
 return false;
 }
 }
 return true;
}
int main() {
 char registration[11]; 
 printf("Enter a vehicle registration number: ");
 scanf("%s", registration);
 if (verifyRegistration(registration)) 
 {
 printf("Accept: Vehicle registration number is valid.\n");
 } 
 else 
 {
 printf("Reject: Vehicle registration number is invalid.\n");
 }
 return 0;
}

#include <stdio.h>
int main() {
 int m, n, p, q;
 printf("Enter the number of rows and columns of the first matrix: ");
 scanf("%d %d", &m, &n);
 printf("Enter the number of rows and columns of the second matrix: ");
 scanf("%d %d", &p, &q);
 if (n != p) {
 printf("Matrix multiplication is not possible. Column of the first matrix must be equal to 
the row of the second matrix.\n");
 return 1;
 }
 int firstMatrix[m][n], secondMatrix[p][q], resultMatrix[m][q];
 printf("Enter elements of the first matrix:\n");
 for (int i = 0; i < m; i++) {
 for (int j = 0; j < n; j++) {
 scanf("%d", &firstMatrix[i][j]);
 }
 }
 printf("Enter elements of the second matrix:\n");
 for (int i = 0; i < p; i++) {
 for (int j = 0; j < q; j++) {
 scanf("%d", &secondMatrix[i][j]);
 }
 }
 // Matrix multiplication
 for (int i = 0; i < m; i++) {
 for (int j = 0; j < q; j++) {
 resultMatrix[i][j] = 0;
 for (int k = 0; k < n; k++) {
 resultMatrix[i][j] += firstMatrix[i][k] * secondMatrix[k][j];
 }
 }
 }
 printf("Resultant matrix after multiplication:\n");
 for (int i = 0; i < m; i++) {
 for (int j = 0; j < q; j++) {
 printf("%d ", resultMatrix[i][j]);
 }
 printf("\n");
 }
 return 0;
}
int sudoku[9][9] = {
 {5, 3, 0, 0, 7, 0, 0, 0, 0},
 {6, 0, 0, 1, 9, 5, 0, 0, 0},
 {0, 9, 8, 0, 0, 0, 0, 6, 0},
 {8, 0, 0, 0, 6, 0, 0, 0, 3},
 {4, 0, 0, 8, 0, 3, 0, 0, 1},
 {7, 0, 0, 0, 2, 0, 0, 0, 6},
 {0, 6, 0, 0, 0, 0, 2, 8, 0},
 {0, 0, 0, 4, 1, 9, 0, 0, 5},
 {0, 0, 0, 0, 8, 0, 0, 7, 9}
 };
Sample Output
Accept
#include <stdio.h>
int isValidSudoku(int board[9][9]) {
 // Check rows
 for (int i = 0; i < 9; i++) {
 int row[10] = {0};
 for (int j = 0; j < 9; j++) {
 if (board[i][j] != 0 && row[board[i][j]] == 1) {
 return 0; // Invalid Sudoku
 }
 row[board[i][j]] = 1;
 }
 }
 // Check columns
 for (int j = 0; j < 9; j++) {
 int col[10] = {0};
 for (int i = 0; i < 9; i++) {
 if (board[i][j] != 0 && col[board[i][j]] == 1) {
 return 0; // Invalid Sudoku
 }
 col[board[i][j]] = 1;
 }
 }
 // Check 3x3 subgrids
 for (int block = 0; block < 9; block++) {
 int subgrid[10] = {0};
 for (int i = block / 3 * 3; i < block / 3 * 3 + 3; i++) {
 for (int j = block % 3 * 3; j < block % 3 * 3 + 3; j++) {
 if (board[i][j] != 0 && subgrid[board[i][j]] == 1) {
 return 0; // Invalid Sudoku
 }
 subgrid[board[i][j]] = 1;
 }
 }
 }
 return 1; // Valid Sudoku
}
int main() {
 int sudoku[9][9] = {
 {5, 3, 0, 0, 7, 0, 0, 0, 0},
 {6, 0, 0, 1, 9, 5, 0, 0, 0},
 {0, 9, 8, 0, 0, 0, 0, 6, 0},
 {8, 0, 0, 0, 6, 0, 0, 0, 3},
 {4, 0, 0, 8, 0, 3, 0, 0, 1},
 {7, 0, 0, 0, 2, 0, 0, 0, 6},
 {0, 6, 0, 0, 0, 0, 2, 8, 0},
 {0, 0, 0, 4, 1, 9, 0, 0, 5},
 {0, 0, 0, 0, 8, 0, 0, 7, 9}
 };
 if (isValidSudoku(sudoku)) {
 printf("Valid Sudoku\n");
 } else {
 printf("Invalid Sudoku\n");
 }
 return 0;
}
#include <stdio.h>
// Define the structure for a student
struct Student 
{
 int studentID;
 char name[50];
 char grade;
 float marks[5];
 float averageMarks;
};
// Function to calculate the average marks for a student
void calculateAverage(struct Student *student) 
{
 float totalMarks = 0.0;
 for (int i = 0; i < 5; i++) 
 {
 totalMarks += student->marks[i];
 }
 student->averageMarks = totalMarks / 5;
}
// Function to assign grades based on average marks
void assignGrades(struct Student *student) 
{
 if (student->averageMarks >= 90) 
 {
 student->grade = 'A';
 } 
 else if (student->averageMarks >= 80) 
 {
 student->grade = 'B';
 } 
 else if (student->averageMarks >= 70) 
 {
 student->grade = 'C';
 } 
 else if (student->averageMarks >= 60) 
 {
 student->grade = 'D';
 } 
 else 
 {
 student->grade = 'F';
 }
}
int main() 
{
 struct Student students[5];
 // Input student information
 for (int i = 0; i < 5; i++) 
 {
 printf("Enter Student ID: ");
 scanf("%d", &students[i].studentID);
 printf("Enter Name: ");
 scanf("%s", students[i].name);
 printf("Enter marks for 5 subjects:\n");
 for (int j = 0; j < 5; j++) {
 printf("Subject %d: ", j + 1);
 scanf("%f", &students[i].marks[j]);
 }
 // Calculate average marks and assign grades
 calculateAverage(&students[i]);
 assignGrades(&students[i]);
 }
 // Display student information
 printf("\nStudent Information:\n");
 for (int i = 0; i < 5; i++) 
 {
 printf("Student ID: %d\n", students[i].studentID);
Data Structure Laboratory Manual
Department of Computer Science and Engineering, Dayananda Sagar University, Bengaluru, 
Karnataka.
 printf("Name: %s\n", students[i].name);
 printf("Average Marks: %.2f\n", students[i].averageMarks);
 printf("Grade: %c\n", students[i].grade);
 printf("\n");
 }
 return 0;
}
#include <stdio.h>
// Define the structure for a student
struct Student 
{
 int studentID;
 char name[50];
 char grade;
 float marks[5];
 float averageMarks;
};
// Function to calculate the average marks for a student
void calculateAverage(struct Student *student) 
{
 float totalMarks = 0.0;
 for (int i = 0; i < 5; i++) 
 {
 totalMarks += student->marks[i];
 }
 student->averageMarks = totalMarks / 5;
}
// Function to assign grades based on average marks
void assignGrades(struct Student *student) 
{
 if (student->averageMarks >= 90) 
 {
 student->grade = 'A';
 } 
 else if (student->averageMarks >= 80) 
 {
 student->grade = 'B';
 } 
 else if (student->averageMarks >= 70) 
 {
 student->grade = 'C';
 } 
 else if (student->averageMarks >= 60) 
 {
 student->grade = 'D';
 } 
 else 
 {
 student->grade = 'F';
 }
}
int main() 
{
 struct Student students[5];
 struct Student *studentPtr = students;
 // Input student information
 for (int i = 0; i < 5; i++) 
 {
 printf("Enter Student ID: ");
 scanf("%d", &studentPtr->studentID);
 printf("Enter Name: ");
 scanf("%s", studentPtr->name);
 printf("Enter marks for 5 subjects:\n");
 for (int j = 0; j < 5; j++) 
 {
 printf("Subject %d: ", j + 1);
 scanf("%f", &studentPtr->marks[j]);
 }
 // Calculate average marks and assign grades
 calculateAverage(studentPtr);
 assignGrades(studentPtr);
 // Move to the next student in the array
 studentPtr++;
 }
 // Reset the pointer to the beginning of the array
 studentPtr = students;
 // Display student information
 printf("\nStudent Information:\n");
 for (int i = 0; i < 5; i++) 
 {
 printf("Student ID: %d\n", studentPtr->studentID);
 printf("Name: %s\n", studentPtr->name);
 printf("Average Marks: %.2f\n", studentPtr->averageMarks);
 printf("Grade: %c\n", studentPtr->grade);
 printf("\n");
 // Move to the next student in the array
 studentPtr++;
 }
 return 0;
}
#include <stdio.h>
#include <stdlib.h>
// Define a structure for a node in the linked list
struct Node {
 int data;
 struct Node* next;
};
// Define a structure for the stack
struct Stack {
 struct Node* top;
};
// Function to create an empty stack
struct Stack* createStack() {
 struct Stack* stack = (struct Stack*)malloc(sizeof(struct Stack));
 stack->top = NULL;
 return stack;
}
// Function to check if the stack is empty
int isEmpty(struct Stack* stack) {
 return (stack->top == NULL);
}
// Function to push an element onto the stack
void push(struct Stack* stack, int data) {
 struct Node* newNode = (struct Node*)malloc(sizeof(struct Node));
 newNode->data = data;
 newNode->next = stack->top;
 stack->top = newNode;
 printf("%d pushed to the stack\n", data);
}
// Function to pop an element from the stack
int pop(struct Stack* stack) {
 if (isEmpty(stack)) {
 printf("Stack is empty. Cannot pop.\n");
 return -1; // Return an invalid value
 }
 struct Node* temp = stack->top;
 int poppedData = temp->data;
 stack->top = temp->next;
 free(temp);
 return poppedData;
}
int main() {
 struct Stack* stack = createStack();
 push(stack, 10);
 push(stack, 20);
 push(stack, 30);
 printf("%d popped from the stack\n", pop(stack));
 printf("%d popped from the stack\n", pop(stack));
 printf("%d popped from the stack\n", pop(stack));
 printf("%d popped from the stack\n", pop(stack)); // Trying to pop from an empty stack
 return 0;
}
#include <stdio.h>
#include <stdlib.h>
#include <string.h>
#define MAX_URL_LENGTH 100
// Structure for a node in the stack
typedef struct Node {
 char url[MAX_URL_LENGTH];
 struct Node* next;
} Node;
// Structure for the stack
typedef struct {
 Node* top;
} Stack;
// Function to initialize an empty stack
void initialize(Stack* stack) {
 stack->top = NULL;
}
// Function to push a URL onto the stack
void push(Stack* stack, const char* url) {
 Node* newNode = (Node*)malloc(sizeof(Node));
 if (newNode == NULL) {
 printf("Memory allocation failed.\n");
 return;
 }
 strncpy(newNode->url, url, MAX_URL_LENGTH);
 newNode->next = stack->top;
 stack->top = newNode;
}
// Function to pop a URL from the stack
void pop(Stack* stack) {
 if (stack->top == NULL) {
 printf("No more URLs in the history.\n");
 return;
 }
 Node* temp = stack->top;
 stack->top = stack->top->next;
 free(temp);
}
void displayCurrentURL(Stack* stack) {
 if (stack->top == NULL) {
 printf("No URL currently loaded.\n");
 } else {
 printf("Current URL: %s\n", stack->top->url);
 }
}
int main() {
 Stack historyStack;
 initialize(&historyStack);
 int choice;
 char url[MAX_URL_LENGTH];
 while (1) {
 printf("\nMenu:\n");
 printf("1. Visit a URL\n");
 printf("2. Go Back\n");
 printf("3. Display Current URL\n");
 printf("4. Exit\n");
 printf("Enter your choice: ");
 scanf("%d", &choice);
 switch (choice) {
 case 1:
 printf("Enter URL to visit: ");
 scanf("%s", url);
 push(&historyStack, url);
 break;
 case 2:
 pop(&historyStack);
 break;
 case 3:
 displayCurrentURL(&historyStack);
 break;
 case 4:
 while (historyStack.top != NULL) {
 pop(&historyStack);
 }
 return 0;
 default:
 printf("Invalid choice. Please try again.\n");
 }
 }
 return 0;
}
#include <stdio.h>
#include <stdlib.h>
struct Node 
{
 int data;
 struct Node* next;
};
struct Queue 
{
 struct Node* front;
 struct Node* rear;
};
struct Queue* createQueue() 
{
 struct Queue* queue = (struct Queue*)malloc(sizeof(struct Queue));
 queue->front = queue->rear = NULL;
 return queue;
}
// Function to check if the queue is empty
int isEmpty(struct Queue* queue) 
{
 return (queue->front == NULL);
}
// Function to enqueue an element to the rear of the queue
void enqueue(struct Queue* queue, int data) 
{
 struct Node* newNode = (struct Node*)malloc(sizeof(struct Node));
 newNode->data = data;
 newNode->next = NULL;
 
 if (isEmpty(queue)) 
 {
 queue->front = queue->rear = newNode;
 } else 
 {
 queue->rear->next = newNode;
 queue->rear = newNode;
 }
}
int dequeue(struct Queue* queue) 
{
 if (isEmpty(queue)) 
 {
 printf("Queue underflow: Cannot dequeue from an empty queue.\n");
 return -1; // Error value
 }
 
 struct Node* temp = queue->front;
 int data = temp->data;
 queue->front = queue->front->next;
 
 free(temp);
 
 return data;
}
void display(struct Queue* queue) 
{
 if (isEmpty(queue)) 
 {
 printf("Queue is empty.\n");
 return;
 }
 
 struct Node* current = queue->front;
 printf("Queue elements: ");
 
 while (current != NULL) 
 {
 printf("%d ", current->data);
 current = current->next;
 }
 
 printf("\n");
}
int main() 
{
 struct Queue* queue = createQueue();
 enqueue(queue, 10);
 enqueue(queue, 20);
 enqueue(queue, 30);
 display(queue);
 printf("Dequeued element: %d\n", dequeue(queue));
 
 display(queue);
 printf("Is the queue empty? %s\n", isEmpty(queue) ? "Yes" : "No");
 return 0;
}
#include <stdio.h>
#include <stdlib.h>
// Structure to represent a customer
struct Customer 
{
 char name[50];
 int age;
 int numTickets;
 struct Customer* next;
};
// Structure to represent the queue
struct Queue 
{
 struct Customer* front;
 struct Customer* rear;
};
// Initialize a queue
struct Queue* createQueue() 
{
 struct Queue* queue = (struct Queue*)malloc(sizeof(struct Queue));
 queue->front = queue->rear = NULL;
 return queue;
}
// Check if the queue is empty
int isEmpty(struct Queue* queue) 
{
 return (queue->front == NULL);
}
// Add a customer to the rear of the queue
void enqueue(struct Queue* queue, struct Customer customer) 
{
 struct Customer* newNode = (struct Customer*)malloc(sizeof(struct Customer));
 *newNode = customer;
 newNode->next = NULL;
 if (isEmpty(queue)) {
 queue->front = queue->rear = newNode;
 } else {
 queue->rear->next = newNode;
 queue->rear = newNode;
 }
}
// Remove and return a customer from the front of the queue
struct Customer dequeue(struct Queue* queue) 
{
 struct Customer emptyCustomer = {"", 0, 0, NULL};
 if (isEmpty(queue)) 
 {
 return emptyCustomer; // Queue is empty
 }
 struct Customer* temp = queue->front;
 struct Customer customer = *temp;
 queue->front = queue->front->next;
 free(temp);
 return customer;
}
int main() 
{
 // Total number of tickets available
 int totalTickets = 100; 
 struct Queue* ticketQueue = createQueue();
 while (totalTickets > 0) 
 {
 struct Customer customer;
 printf("Enter customer name: ");
 scanf("%s", customer.name);
 printf("Enter customer age: ");
 scanf("%d", &customer.age);
 printf("Enter number of tickets needed: ");
 scanf("%d", &customer.numTickets);
 if (customer.numTickets <= totalTickets) 
 {
 totalTickets -= customer.numTickets;
 enqueue(ticketQueue, customer);
 printf("Tickets sold to %s (%d tickets remaining)\n", customer.name, totalTicket);
 } 
 else 
 {
 printf("Insufficient tickets available. Tickets not sold to %s\n", customer.name);
 }
 printf("Do you want to add another customer? (1 for yes, 0 for no): ");
 int choice;
 scanf("%d", &choice);
 if (choice != 1) 
 {
 break;
 }
 }
 printf("Houseful! All tickets are sold.\n");
 return 0;
}
 
 
 
 
 
 
 
 
 
 
