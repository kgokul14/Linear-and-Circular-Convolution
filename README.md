# EXP 2 : Linear and Circular Convolution

## AIM: 

 To perform Linear and Circular Convolution for two given sequence using SCILAB. 

## APPARATUS REQUIRED: 
PC installed with SCILAB. 

## PROGRAM (Linear Convolution): 
```
clc;
clear;
clf;

// Define sequences
x = [1 2 3 4];      // First sequence
h = [1 1 1];        // Second sequence

lx = length(x);
lh = length(h);

// Length of output
ly = lx + lh - 1;

// Initialize output
y = zeros(1, ly);

// Manual convolution
for n = 1:ly
    for k = 1:lx
        if (n-k+1 > 0) & (n-k+1 <= lh) then
            y(n) = y(n) + x(k) * h(n-k+1);
        end
    end
end

// Display results
disp("First sequence x(n) = " + string(x));
disp("Second sequence h(n) = " + string(h));
disp("Linear Convolution y(n) = " + string(y));

// Plot results
subplot(3,1,1);
plot2d3(0:lx-1, x);
xtitle("First Sequence x(n)","n","x(n)");

subplot(3,1,2);
plot2d3(0:lh-1, h);
xtitle("Second Sequence h(n)","n","h(n)");

subplot(3,1,3);
plot2d3(0:ly-1, y);
xtitle("Convolution Result y(n)","n","y(n)");
```
## PROGRAM (Circular Convolution): 

```
clc;
clear;
clf;

// Input sequences
x = [1 5 2 4];
h = [1 2 4 3];
N = length(x);   // Circular length

// FFT Method
X = fft(x, -1);   // Forward FFT
H = fft(h, -1);

Y = X .* H;       // Multiply in frequency domain
y = real(fft(Y, 1));  // Inverse FFT and keep real part

// Display
disp("Sequence x(n) = " + string(x));
disp("Sequence h(n) = " + string(h));
disp("Circular Convolution y(n) = " + string(y));

// Index
n = 0:N-1;

// Plot x(n)
subplot(3,1,1);
plot2d3(n, x);
xtitle("Sequence x(n)", "n", "x(n)");
a = gca();
a.data_bounds = [-1, min(x)-1; N, max(x)+1];

// Plot h(n)
subplot(3,1,2);
plot2d3(n, h);
xtitle("Sequence h(n)", "n", "h(n)");
a = gca();
a.data_bounds = [-1, min(h)-1; N, max(h)+1];

// Plot y(n)
subplot(3,1,3);
plot2d3(n, y);
xtitle("Circular Convolution Result y(n)", "n", "y(n)");
a = gca();
a.data_bounds = [-1, min(y)-1; N, max(y)+1];
```

## OUTPUT (Linear Convolution): 

<img width="767" height="726" alt="image" src="https://github.com/user-attachments/assets/13f0c071-e82c-4142-9663-9a965c2762f8" />


## OUTPUT (Circular Convolution): 
<img width="763" height="734" alt="image" src="https://github.com/user-attachments/assets/376bda5e-a01f-4636-9c44-addfc48b8e24" />
<img width="1429" height="194" alt="image" src="https://github.com/user-attachments/assets/f6bd4fa0-49f8-42a3-b002-efc41f1c38ab" />



## RESULT: 
Thus, the Linear and Circular Convolution of the given sequences were successfully computed and verified.
