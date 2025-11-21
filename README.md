# Design-of-FIR-Filters-using-hamming-window

# DESIGN OF LOW PASS FIR DIGITAL FILTER 

# AIM: 
          
  To generate design of high pass FIR digital filter using SCILAB 

# APPARATUS REQUIRED: 

  PC Installed with SCILAB 

# PROGRAM:
```c

clear;
close;

// Filter specifications
M = 50;            // Filter order
fc = 0.2;          // Normalized cutoff frequency (0 to 0.5)

// Sample points
n = 0:M;

// Ideal impulse response of High Pass Filter
hd = zeros(1, M+1);
for i = 1:M+1
    if i == (M/2 + 1) then
        hd(i) = 1 - 2*fc;
    else
        hd(i) = (-sin(2*%pi*fc*(i - (M/2 + 1)))) / (%pi*(i - (M/2 + 1)));
    end
end

// Hamming window
w = 0.54 - 0.46 * cos(2*%pi*n/M);

// Apply window
h = hd .* w;

// Plot Impulse Response
figure(1);
plot(n, h);
xlabel("n");
ylabel("h(n)");
title("Impulse Response of High Pass FIR Filter using Hamming Window");
xgrid();

// Frequency Response
[H, f] = frmag(h, 512);
figure(2);
plot(f, H);
xlabel("Normalized Frequency");
ylabel("|H(f)|");
title("Magnitude Response of High Pass FIR Filter using Hamming Window");
xgrid();

```

# OUTPUT:

<img width="812" height="398" alt="4" src="https://github.com/user-attachments/assets/202a89b7-8890-4b0b-93db-d04227cb1fbb" />


<img width="815" height="405" alt="41" src="https://github.com/user-attachments/assets/c8d343d1-1708-434f-995d-fa8af1c713b5" />


# RESULT:

The High-Pass FIR filter was successfully designed and plotted using the Hamming window in Scilab.
