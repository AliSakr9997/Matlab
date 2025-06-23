# Matlab

# Introduction
This document presents a curated set of notes taken during my study of MATLAB across 11 structured lectures. It summarizes key concepts, functions, and examples essential for understanding the language and its applications.

Designed to serve as a clear and practical reference, these notes aim to support students and beginners in building a solid foundation in MATLAB programming.

Use this guide for revision, project work, or as a quick reference throughout your learning journey.


# MATLAB Study Guide - Lecture Notes

## Table of Contents
1. [Basic Commands and Variables](#basic-commands-and-variables)
2. [Data Types and Formatting](#data-types-and-formatting)
3. [Mathematical Operations](#mathematical-operations)
4. [Vectors and Arrays](#vectors-and-arrays)
5. [Matrices](#matrices)
6. [Control Structures](#control-structures)
7. [Functions and Error Handling](#functions-and-error-handling)
8. [GUI Programming](#gui-programming)
9. [Plotting and Visualization](#plotting-and-visualization)
10. [Advanced Plotting](#advanced-plotting)
11. [Polynomials and Curve Fitting](#polynomials-and-curve-fitting)
12. [Control Systems](#control-systems)
13. [Block Diagram Reduction](#block-diagram-reduction)
14. [Symbolic Mathematics](#symbolic-mathematics)
15. [System Conversions](#system-conversions)
16. [File Operations](#file-operations)

---

## 1. Basic Commands and Variables

### Variable Assignment
```matlab
x = 6     % Normal assignment (displays result)
x = 6;    % Silent assignment (doesn't display result)
```

### Workspace Management
```matlab
who       % Show variable names
whos      % Show variables with detailed information
clc       % Clear command window
clear     % Clear all variables
clear a b c  % Remove specific variables (a, b, c)
```

### Help and Documentation
```matlab
help function_name    % Show help for a function
lookfor keyword      % Find all functions related to keyword
doc function_name    % Open full documentation
```

**Note:** MATLAB is case-sensitive!

---

## 2. Data Types and Formatting

### Integer Data Types
```matlab
a = int8(5)    % 8-bit signed integer (-128 to 127)
a = uint8(5)   % 8-bit unsigned integer (0 to 255)
a = int16(5)   % 16-bit signed integer
a = int32(5)   % 32-bit signed integer
a = int64(5)   % 64-bit signed integer
```

### Floating Point Types
```matlab
a = single(5.5)  % Single precision (32-bit)
a = double(5.5)  % Double precision (64-bit) - default
a = char('A')    % Character data type
```

### Number Display Formats
```matlab
format short  % Display 4 digits after decimal point
format long   % Display 16 digits after decimal point
```

### Rounding Functions
```matlab
fix(a)    % Round towards zero
floor(a)  % Round towards negative infinity
ceil(a)   % Round towards positive infinity
round(a)  % Round to nearest integer
```

---

## 3. Mathematical Operations

### Complex Numbers
```matlab
x = 6 + 7i              % Create complex number
abs(x)                  % Magnitude: sqrt(6² + 7²)
angle(x)                % Phase angle in radians
real(x)                 % Real part only
imag(x)                 % Imaginary part only
y = complex(7, 8)       % Create complex number: 7 + 8i
```

### Mathematical Functions
```matlab
pi                      % π ≈ 3.14159
log10(x)               % Logarithm base 10
log(x)                 % Natural logarithm (base e)
sqrt(x)                % Square root
exp(x)                 % e^x
factorial(n)           % n!
```

### Trigonometric Functions
```matlab
% Radians
cos(a), sin(a), tan(a)       % Basic trig functions
acos(a), asin(a), atan(a)    % Inverse trig functions

% Degrees
cosd(a), sind(a), tand(a)    % Trig functions in degrees
acosd(a), asind(a), atand(a) % Inverse trig in degrees
```

---

## 4. Vectors and Arrays

### Creating Vectors
```matlab
x = [2 3 222 22 2]     % Row vector
x = 1:10               % Vector from 1 to 10, step 1
x = 1:2:10             % Vector from 1 to 10, step 2
x = 1:0.5:5            % Vector with decimal step
```

### Specialized Vector Creation
```matlab
linspace(start, stop, n)  % n evenly spaced points from start to stop
logspace(a, b, n)        % n points between 10^a and 10^b
```

### Vector Operations
```matlab
x(5)           % Access 5th element (1-indexed)
x(2:8)         % Elements 2 through 8
x(2:2:8)       % Elements 2, 4, 6, 8
max(x)         % Maximum value
min(x)         % Minimum value
mean(x)        % Average value
length(x)      % Number of elements
sum(x)         % Sum of all elements
x .* 2         % Multiply each element by 2 (element-wise)
```

### Sorting
```matlab
sort(x)              % Ascending order (default)
sort(x, 'ascend')    % Ascending order
sort(x, 'descend')   % Descending order
```

---

## 5. Matrices

### Creating Matrices
```matlab
x = [1 2 3; 4 5 6; 7 8 9]  % 3×3 matrix
rand(m, n)                  % m×n matrix with random numbers
ones(n)                     % n×n matrix of ones
ones(m, n)                  % m×n matrix of ones
zeros(n)                    % n×n matrix of zeros
eye(n)                      % n×n identity matrix
repmat(value, m, n)         % m×n matrix filled with value
```

### Matrix Operations
```matlab
% Standard matrix operations
A + B, A - B    % Addition, subtraction
A * B           % Matrix multiplication
A / B           % Matrix division

% Element-wise operations
A .* B          % Element-wise multiplication
A ./ B          % Element-wise division

% Matrix functions
inv(A)          % Matrix inverse
det(A)          % Determinant
A'              % Transpose
```

### Matrix Manipulation
```matlab
A(3,3) = 10           % Change element at row 3, column 3
A(1,:) = [4 3 5]      % Change entire first row
A(:,2) = [44; 53; 55] % Change entire second column
reshape(A, m, n)      % Reshape matrix (total elements must match)
triu(A)               % Upper triangular part
tril(A)               % Lower triangular part
```

### Matrix Information
```matlab
[m, n] = size(A)   % Get dimensions (m rows, n columns)
length(A)          % Maximum of rows and columns
numel(A)           % Total number of elements
```

---

## 6. Control Structures

### Comments
```matlab
% This is a single-line comment
```

### If-Else Statements
```matlab
score = 85;
if score > 90
    grade = 'A';
    disp('Excellent')
elseif score >= 80
    grade = 'B';
    disp('Good')
else
    grade = 'C';
    disp('Average')
end
```

### Switch-Case Statements
```matlab
grade = 'B';
switch grade
    case 'A'
        disp('Excellent')
    case 'B'
        disp('Good')
    case 'C'
        disp('Average')
    otherwise
        disp('Invalid grade')
end
```

### For Loops
```matlab
% Basic for loop
for i = 1:10
    disp(i)
    pause(0.5)  % Pause for 0.5 seconds
end

% Nested for loop example
matrix = [1 2 3; 4 5 6; 7 8 9];
[rows, cols] = size(matrix);
for i = 1:rows
    for j = 1:cols
        disp(matrix(i,j))
        pause(0.1)
    end
end
```

### While Loops
```matlab
count = 1;
while count <= 10
    disp(count)
    count = count + 1;
    pause(0.1)
end
```

---

## 7. Functions and Error Handling

### Function Definition
```matlab
function [sum_val, mean_val, min_val, max_val] = analyze_data(a, b)
    c = a .* b;                    % Element-wise multiplication
    sum_val = sum(c(:));           % Sum of all elements
    mean_val = mean(c(:));         % Mean of all elements
    max_val = max(c(:));           % Maximum value
    min_val = min(c(:));           % Minimum value
end
```

### Try-Catch Error Handling
```matlab
value1 = 2;
try
    value2 = value1 * undefined_variable;
catch
    value2 = 0;
    disp('Error occurred, using default value')
end
```

### Structures
```matlab
person.name = "John";
person.age = 25;
person.city = "New York";
```

---

## 8. GUI Programming

### Getting Values from GUI Components
```matlab
% Inside a pushbutton callback function
length_val = str2double(get(handles.length_input, 'string'));
width_val = str2double(get(handles.width_input, 'string'));
area = length_val * width_val;

% Set result in output field
set(handles.area_output, 'string', num2str(area));
```

### GUI Control Functions
```matlab
% Turn off radio buttons
function radio_off(handles)
    set(handles.length_radio, 'value', 0);
    set(handles.mass_radio, 'value', 0);
end

% Disable popup menus
function popup_off(handles)
    set(handles.length_popup, 'enable', 'off');
    set(handles.mass_popup, 'enable', 'off');
    set(handles.output_edit, 'visible', 'off');
end
```

### Switch Case for GUI
```matlab
selected = get(hObject, 'value');
input_val = str2double(get(handles.input_edit, 'string'));

switch selected
    case 1
        set(handles.output_edit, 'visible', 'off')
    case 2
        result = input_val / 100;  % Convert to meters
    case 3
        result = input_val / 10;   % Convert to decimeters
    case 4
        result = input_val * 10;   % Convert to millimeters
end

if selected ~= 1
    set(handles.output_edit, 'visible', 'on', 'string', num2str(result))
end
```

---

## 9. Plotting and Visualization

### Basic Plotting
```matlab
x = linspace(0, 2*pi, 100);
y = sin(x);
z = cos(x);

% Plot single line
plot(x, y, 'r-', 'LineWidth', 2)

% Plot multiple lines
plot(x, y, 'ro-', x, z, 'bs-', 'LineWidth', 1.5)

% Hold on to add more plots
plot(x, y, 'ro-', 'LineWidth', 0.5)
hold on
plot(x, z, 'bs-', 'LineWidth', 0.5)
```

### Plot Formatting
```matlab
grid on                    % Add grid
box on                     % Add box around plot
title('My Plot')           % Add title
xlabel('X-axis Label')     % X-axis label
ylabel('Y-axis Label')     % Y-axis label
legend('Sin(x)', 'Cos(x)') % Add legend

% Advanced formatting
xlabel('X-axis', 'Interpreter', 'tex', 'FontSize', 20, 'FontName', 'Times')
legend({'Sin(x)', 'Cos(x)'}, 'Location', 'southwest', 'Orientation', 'vertical')
```

### Line Styles and Markers
- `'-'` solid line, `'--'` dashed line, `':'` dotted line
- `'o'` circles, `'*'` asterisks, `'s'` squares, `'p'` pentagrams
- `'r'` red, `'g'` green, `'b'` blue, `'k'` black

---

## 10. Advanced Plotting

### Subplots
```matlab
x = linspace(0, 2*pi, 100);
y = sin(x); z = cos(x); a = tan(x); b = exp(-x);

subplot(2, 2, 1)
plot(x, y, 'r:p')
title('Sine')

subplot(2, 2, 2)
plot(x, z, 'g-*')
title('Cosine')

subplot(2, 2, 3)
plot(x, a, 'k--', 'LineWidth', 1.5)
title('Tangent')

subplot(2, 2, 4)
plot(x, b, 'b-o')
title('Exponential Decay')
```

### Dual Y-axis Plots
```matlab
[ax, h1, h2] = plotyy(x, y, x, a, 'plot');
set(get(ax(1), 'ylabel'), 'string', 'Left Y-axis')
set(get(ax(2), 'ylabel'), 'string', 'Right Y-axis')
xlabel('X-axis')
set(h1, 'LineWidth', 2, 'LineStyle', ':')
set(h2, 'LineWidth', 2, 'LineStyle', '--')
```

### Specialized Plot Types
```matlab
% 3D plotting
plot3(x, y, z)

% Bar graphs
bar(data)      % 2D bar graph
bar3(data)     % 3D bar graph

% Other plot types
area(data)     % Area plot
stairs(x, y)   % Stairs plot
```

### Logarithmic Plots
| Function | X-axis | Y-axis | Use Case |
|----------|--------|--------|----------|
| `plot` | Linear | Linear | Standard data |
| `semilogy` | Linear | Log | Exponential growth/decay |
| `semilogx` | Log | Linear | Wide range of x values |
| `loglog` | Log | Log | Power relationships |

---

## 11. Polynomials and Curve Fitting

### Curve Fitting
```matlab
x = [1 2 3 4 5];        % Input data
y = [2 7 13 21 32];     % Output data
n = 2;                  % Degree of polynomial
p = polyfit(x, y, n);   % Fit polynomial
```

### Polynomial Roots
```matlab
% Find roots of polynomial
p = [1 -12 25 116];     % Coefficients of s^3 - 12s^2 + 25s + 116
roots_p = roots(p);

% Create polynomial from roots
roots_given = [1 2 3];
p = poly(roots_given);
```

### Polynomial Evaluation
```matlab
p = [2 -4 3 5];         % Polynomial coefficients
x = 2;                  % Point to evaluate
y = polyval(p, x);      % Evaluate polynomial at x = 2
```

### Polynomial Operations
```matlab
p1 = [1 2];             % x + 2
p2 = [1 3];             % x + 3

% Addition and subtraction
sum_p = p1 + p2;        % Note: polynomials must have same length

% Multiplication
product = conv(p1, p2); % Convolution for multiplication

% Division
[quotient, remainder] = deconv(product, p1);
```

### Calculus Operations
```matlab
p = [1 -12 25 116];            % Original polynomial
derivative_p = polyder(p);      % Derivative
integral_p = polyint(p, C);     % Integration with constant C
```

---

## 12. Control Systems

### Transfer Functions
```matlab
num = [2 4 1];              % Numerator coefficients
den = [3 8 9 10 0];         % Denominator coefficients
printsys(num, den);         % Display transfer function
```

### Partial Fraction Expansion
```matlab
[residues, poles, direct] = residue(num, den);
```

### Zero-Pole-Gain Form
```matlab
k = 20;                     % Gain
z = [-2; -4];              % Zeros
p = [-3; -2+5i; -2-5i];    % Poles
sys = zpk(z, p, k);        % Create system
```

### State-Space Representation
```matlab
A = [-5 -5; 1 0];          % State matrix
B = [1; 0];                % Input matrix
C = [0 5];                 % Output matrix
D = 0;                     % Feedthrough matrix

% Labels for documentation
u_label = {'Input Voltage'};
y_label = {'Angular Speed'};
x_label = {'x1'; 'x2'};

sys_ss = ss(A, B, C, D);
printsys(A, B, C, D, u_label, y_label, x_label);
```

### System Response
```matlab
num = [1];
den = [1 2 1];
step(num, den);        % Step response
impulse(num, den);     % Impulse response

% For discrete systems
num_z = [0.12867*1.4, 0.91242*1.4];
den_z = [1, -1.4, 0.8];
tf_z = tf(num_z, den_z, 0.1);  % Sampling time = 0.1s
```

---

## 13. Block Diagram Reduction

### Series Connection
```matlab
% First block
num1 = [3 6];
den1 = [1 7 0];

% Second block
num2 = [5];
den2 = [1 2 10];

% Series combination
[num_total, den_total] = series(num1, den1, num2, den2);
printsys(num_total, den_total);
```

### Parallel Connection
```matlab
[num_total, den_total] = parallel(num1, den1, num2, den2);
```

### Feedback Connection
```matlab
% Feedback block
num_h = [1 2];
den_h = [1 10];

% With feedback transfer function
[num_cl, den_cl] = feedback(num1, den1, num_h, den_h, -1);

% Unity feedback (H = 1)
[num_cl, den_cl] = cloop(num1, den1, -1);
% OR
[num_cl, den_cl] = feedback(num1, den1, 1, 1, -1);
```

---

## 14. Symbolic Mathematics

### Symbolic Variables
```matlab
syms x y z              % Declare symbolic variables
x = sym('x')           % Alternative declaration
```

### Symbolic Operations
```matlab
syms x y
expr = (x + y)^2;

expand(expr)           % Expand: x^2 + 2*x*y + y^2
factor(expr)           % Factor expression
simplify(expr)         % Simplify expression
```

### Substitution
```matlab
subs(expr, x, 0)             % Substitute x = 0
subs(expr, x, y^2)           % Substitute x = y^2
subs(expr, {x, y}, {2, 5})   % Substitute x = 2, y = 5
```

### Calculus
```matlab
syms x
f = x^3 + 6*x^2 - 10*x;

% Differentiation
df = diff(f, x);         % First derivative
d2f = diff(f, x, 2);     % Second derivative

% Integration
F = int(f, x);           % Indefinite integral
F_def = int(f, x, 0, 2); % Definite integral from 0 to 2

% Limits
limit(f/x, x, 0);        % Limit as x approaches 0
```

### Laplace Transforms
```matlab
syms t s
f = exp(-2*t) * cos(3*t);

F = laplace(f, t, s);    % Laplace transform
f_inv = ilaplace(F, s, t); % Inverse Laplace transform
```

---

## 15. System Conversions

### State-Space to Transfer Function
```matlab
A = [-5 -5; 1 0];
B = [1; 0];
C = [0 5];
D = 0;

[num, den] = ss2tf(A, B, C, D);
printsys(num, den);
```

### Transfer Function to State-Space
```matlab
num = [5];
den = [1 5 5];
[A, B, C, D] = tf2ss(num, den);
```

### Zero-Pole-Gain Conversions
```matlab
% ZPK to Transfer Function
k = 10;
z = [-1; -2];
p = [0; -3; -4; -5];
[num, den] = zp2tf(z, p, k);

% Transfer Function to ZPK
[z, p, k] = tf2zp(num, den);

% ZPK to State-Space
[A, B, C, D] = zp2ss(z, p, k);
```

### Pole-Zero Cancellation
```matlab
num = [1 -1 0];
den = [1 0 0 -1];
[num_reduced, den_reduced] = minreal(num, den);
```

### Continuous to Discrete Conversion
```matlab
num_s = [1];
den_s = [1 1];
T = 0.1;  % Sampling time
[num_z, den_z] = c2d(num_s, den_s, T);
```

### Discrete to Continuous Conversion
```matlab
A_d = [1 0; 0.1 0.9];
B_d = [0.2; 0.7];
C_d = [1 0; 0 1];
D_d = [0; 0];
T = 0.001;

sys_d = ss(A_d, B_d, C_d, D_d, T);
sys_c = d2c(sys_d);

A_c = sys_c.A;
B_c = sys_c.B;
C_c = sys_c.C;
D_c = sys_c.D;
```

---

## 16. File Operations

### Writing to File
```matlab
t = linspace(0, 2*pi, 5);
data = [t; sin(t)];  % 2×5 matrix

% Open file for writing
file_id = fopen('data.txt', 'w');
fprintf(file_id, '%f %f\n', data);  % Write data
fclose(file_id);  % Close file
```

### Reading from File
```matlab
file_id = fopen('data.txt', 'r');
data = fscanf(file_id, '%f %f', [2 Inf]);  % Read 2 rows, unlimited columns
fclose(file_id);
```

### Appending to File
```matlab
n = linspace(0, 2*pi, 10);
new_data = [n; n.^2; sin(n)];  % 3×10 matrix

file_id = fopen('data.txt', 'a');  % Open for appending
fprintf(file_id, '\n--- New Data ---\n');
fprintf(file_id, '%f %f %f\n', new_data);
fclose(file_id);
```

### File Access Modes
- `'r'` - Read only
- `'w'` - Write (overwrites existing file)
- `'a'` - Append to end of file
- `'r+'` - Read and write

---
