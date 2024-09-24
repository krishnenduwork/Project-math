#include <stdio.h>
#include <math.h>

// Function to display the main menu
void displayMenu() {
    printf("Select the type of operation:\n");
    printf("1. Arithmetic Operations\n");
    printf("2. Algebraic Operations\n");
    printf("3. Quadratic Equation Solver\n");
    printf("4. Trigonometric Operations\n");
    printf("5. Exit\n");
}

// Function for arithmetic operations
void arithmeticOperations() {
    int choice;
    double num1, num2, result;

    printf("\nArithmetic Operations:\n");
    printf("1. Addition (+)\n");
    printf("2. Subtraction (-)\n");
    printf("3. Multiplication (*)\n");
    printf("4. Division (/)\n");
    printf("5. Modulus (for integers) (%%)\n");
    printf("Enter your choice: ");
    scanf("%d", &choice);

    if (choice == 5) {
        int int1, int2;
        printf("Enter two integers: ");
        scanf("%d %d", &int1, &int2);
        result = int1 % int2;
        printf("Result: %d %% %d = %.0f\n", int1, int2, result);
    } else {
        printf("Enter two numbers: ");
        scanf("%lf %lf", &num1, &num2);

        switch (choice) {
            case 1: result = num1 + num2; break;
            case 2: result = num1 - num2; break;
            case 3: result = num1 * num2; break;
            case 4: 
                if (num2 != 0) 
                    result = num1 / num2;
                else {
                    printf("Error: Division by zero.\n");
                    return;
                }
                break;
            default: 
                printf("Invalid choice!\n");
                return;
        }
        printf("Result: %.2lf\n", result);
    }
}

// Function for algebraic operations (polynomial evaluation)
void algebraicOperations() {
    int degree;
    double x, result = 0;

    printf("\nAlgebraic Operations (Polynomial Evaluation):\n");
    printf("Enter the degree of the polynomial: ");
    scanf("%d", &degree);

    double coefficients[degree + 1];
    printf("Enter the coefficients (from highest degree to constant):\n");
    for (int i = 0; i <= degree; i++) {
        printf("Coefficient of x^%d: ", degree - i);
        scanf("%lf", &coefficients[i]);
    }

    printf("Enter the value of x: ");
    scanf("%lf", &x);

    for (int i = 0; i <= degree; i++) {
        result += coefficients[i] * pow(x, degree - i);
    }

    printf("Result of the polynomial at x = %.2lf is: %.2lf\n", x, result);
}

// Function to solve quadratic equations: ax^2 + bx + c = 0
void solveQuadratic() {
    double a, b, c, discriminant, root1, root2, realPart, imaginaryPart;

    printf("\nQuadratic Equation Solver: ax^2 + bx + c = 0\n");
    printf("Enter coefficients a, b, and c: ");
    scanf("%lf %lf %lf", &a, &b, &c);

    discriminant = b * b - 4 * a * c;

    if (discriminant > 0) {
        root1 = (-b + sqrt(discriminant)) / (2 * a);
        root2 = (-b - sqrt(discriminant)) / (2 * a);
        printf("Roots are real and different.\n");
        printf("Root 1 = %.2lf\n", root1);
        printf("Root 2 = %.2lf\n", root2);
    } else if (discriminant == 0) {
        root1 = -b / (2 * a);
        printf("Roots are real and the same.\n");
        printf("Root 1 = Root 2 = %.2lf\n", root1);
    } else {
        realPart = -b / (2 * a);
        imaginaryPart = sqrt(-discriminant) / (2 * a);
        printf("Roots are complex and different.\n");
        printf("Root 1 = %.2lf + %.2lfi\n", realPart, imaginaryPart);
        printf("Root 2 = %.2lf - %.2lfi\n", realPart, imaginaryPart);
    }
}

// Function for trigonometric operations
void trigonometricOperations() {
    int choice;
    double angle, result;

    printf("\nTrigonometric Operations:\n");
    printf("1. Sine (sin)\n");
    printf("2. Cosine (cos)\n");
    printf("3. Tangent (tan)\n");
    printf("4. Cotangent (cot)\n");
    printf("5. Secant (sec)\n");
    printf("6. Cosecant (csc)\n");
    printf("Enter your choice: ");
    scanf("%d", &choice);

    printf("Enter the angle in degrees: ");
    scanf("%lf", &angle);

    // Convert degrees to radians
    angle = angle * M_PI / 180;

    switch (choice) {
        case 1: result = sin(angle); break;
        case 2: result = cos(angle); break;
        case 3: result = tan(angle); break;
        case 4: 
            if (tan(angle) != 0) result = 1 / tan(angle); 
            else {
                printf("Error: Undefined result.\n");
                return;
            }
            break;
        case 5: 
            if (cos(angle) != 0) result = 1 / cos(angle); 
            else {
                printf("Error: Undefined result.\n");
                return;
            }
            break;
        case 6: 
            if (sin(angle) != 0) result = 1 / sin(angle); 
            else {
                printf("Error: Undefined result.\n");
                return;
            }
            break;
        default: 
            printf("Invalid choice!\n");
            return;
    }

    printf("Result: %.4lf\n", result);
}

// Main function
int main() {
    int choice;

    while (1) {
        displayMenu();
        printf("Enter your choice: ");
        scanf("%d", &choice);

        switch (choice) {
            case 1:
                arithmeticOperations();
                break;
            case 2:
                algebraicOperations();
                break;
            case 3:
                solveQuadratic();
                break;
            case 4:
                trigonometricOperations();
                break;
            case 5:
                printf("Exiting the program.\n");
                return 0;
            default:
                printf("Invalid choice! Please try again.\n");
        }

        printf("\n");
    }

    return 0;
}
