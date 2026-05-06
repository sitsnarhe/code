clc; clear; 
fm=5; 
t=0:0.0001:1; 
x=sin(2*pi*fm*t); 
%% Sampling Rates 
fs1=5; 
fs2=10; 
fs3=25; 
t1=0:1/fs1:1; 
t2=0:1/fs2:1; 
t3=0:1/fs3:1; 
x1=sin(2*pi*fm*t1); 
x2=sin(2*pi*fm*t2); 
x3=sin(2*pi*fm*t3); 
subplot(4,1,1); plot(t,x); title('Original Signal'); 
subplot(4,1,2); stem(t1,x1); title('Below Nyquist'); 
subplot(4,1,3); stem(t2,x2); title('At Nyquist'); 
subplot(4,1,4); stem(t3,x3); title('Above Nyquist');

