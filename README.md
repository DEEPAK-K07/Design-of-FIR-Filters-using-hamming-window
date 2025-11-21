# Design-of-FIR-Filters-using-hamming-window

# DESIGN OF LOW PASS AND HIGH PASS FIR DIGITAL FILTER 

# AIM: 
          
  To generate design of low pass and high pass FIR digital filter using SCILAB 

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

<img width="823" height="416" alt="4L" src="https://github.com/user-attachments/assets/46ab012b-f6c5-4089-87d1-68fede1bb792" />


<img width="818" height="409" alt="4H" src="https://github.com/user-attachments/assets/23f2a72f-b54a-437d-96c3-69bbf3b8986b" />


# RESULT:

The Low-Pass and High-Pass FIR filter was successfully designed and plotted using the Hamming window in Scilab.
