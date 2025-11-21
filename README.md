# Design-of-FIR-Filters-using-hamming-window

# DESIGN OF LOW PASS AND HIGH PASS FIR DIGITAL FILTER 

# AIM: 
          
  To generate design of low pass and high pass FIR digital filter using SCILAB 

# APPARATUS REQUIRED: 

  PC Installed with SCILAB 

# PROGRAM:

__LOW-PASS FIR FILTER__

```c
clc;
clear;
close;

// Low Pass FIR Filter using Hamming Window
N = 50;              // Filter length
fc = 0.4;            // Normalized cutoff frequency (fc = Fcutoff / (Fs/2))
n = 0:N-1;
alpha = (N-1)/2;

// Hamming window
w = 0.54 - 0.46*cos(2*%pi*n/(N-1));

// Ideal Low Pass Filter Impulse Response
hd = zeros(1, N);
for i = 1:N
    if (i-1) == alpha then
        hd(i) = 2*fc;
    else
        hd(i) = sin(2*%pi*fc*(i-1-alpha)) / (%pi*(i-1-alpha));
    end
end

// Multiply by window
h = hd .* w;

// Frequency Response
[H, f] = frmag(h, 512);

// Plot
figure;
subplot(2,1,1);
plot(f, 20*log10(abs(H)));
xlabel('Normalized Frequency');
ylabel('Magnitude (dB)');
title('LOW PASS FIR FILTER (Hamming Window)');

subplot(2,1,2);
plot(f, atan(imag(H), real(H)));
xlabel('Normalized Frequency');
ylabel('Phase (radians)');
title('Phase Response');

```

__HIGH-PASS FIR FILTER__

```c

clc;
clear;
close;

// High Pass FIR Filter using Hamming Window
N = 51;              // Filter length
fc = 0.3;            // Normalized cutoff frequency (fc = Fcutoff / (Fs/2))
n = 0:N-1;
alpha = (N-1)/2;

// Hamming window
w = 0.54 - 0.46*cos(2*%pi*n/(N-1));

// Ideal High Pass Filter Impulse Response
hd = zeros(1, N);
for i = 1:N
    if (i-1) == alpha then
        hd(i) = 1 - 2*fc;
    else
        hd(i) = -sin(2*%pi*fc*(i-1-alpha)) / (%pi*(i-1-alpha));
    end
end

// Multiply by window
h = hd .* w;

// Frequency Response
[H, f] = frmag(h, 512);

// Plot
figure;
subplot(2,1,1);
plot(f, 20*log10(abs(H)));
xlabel('Normalized Frequency');
ylabel('Magnitude (dB)');
title('HIGH PASS FIR FILTER (Hamming Window)');

subplot(2,1,2);
plot(f, atan(imag(H), real(H)));
xlabel('Normalized Frequency');
ylabel('Phase (radians)');
title('Phase Response');


```

# OUTPUT:

<img width="823" height="416" alt="4L" src="https://github.com/user-attachments/assets/46ab012b-f6c5-4089-87d1-68fede1bb792" />


<img width="818" height="409" alt="4H" src="https://github.com/user-attachments/assets/23f2a72f-b54a-437d-96c3-69bbf3b8986b" />


# RESULT:

The Low-Pass and High-Pass FIR filter was successfully designed and plotted using the Hamming window in Scilab.
