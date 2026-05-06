clc; clear; 
t = 0:0.001:1; 
x = sin(2*pi*5*t); 
%% PCM 
n = 8; 
L = 2^n; 
xq = round((x+1)/2*(L-1)); 
x_rec = (xq/(L-1))*2 - 1; 
noise_pcm = x - x_rec; 
SNR_PCM = 10*log10(mean(x.^2)/mean(noise_pcm.^2)); 
%% Delta Modulation 
step = 0.1; 
dm = zeros(size(x)); 
for i=2:length(x) 
    if x(i) > dm(i-1) 
        dm(i)=dm(i-1)+step; 
    else 
        dm(i)=dm(i-1)-step; 
    end 
end 
noise_dm = x-dm; 
SNR_DM = 10*log10(mean(x.^2)/mean(noise_dm.^2)); 
disp(['SNR PCM = ',num2str(SNR_PCM),' dB']); 
disp(['SNR DM = ',num2str(SNR_DM),' dB']);

