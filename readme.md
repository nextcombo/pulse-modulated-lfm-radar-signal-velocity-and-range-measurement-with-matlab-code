# Pulse-modulated LFM radar signal velocity and range measurement [with MATLAB code]

This project utilizes 32 pulse-modulated linear frequency modulation continuous wave transmission signals, incorporating distance time delay and Doppler shift information into the single target echo signal. After digital down-conversion, pulse pressure and MTD processing are performed to detect distance and velocity information.
Partial code display
% =================================================================================== %32 Pulse Single Target Time Domain Pressure and Doppler Frequency Shift % =================================================================================== %% Clear all variables and graphics close all; clear all; clc; %% Radar parameters Tp=40e-6; % Pulse width 40us T=20e-5; %Pulse repetition period 200us B=20e6; % Linear Frequency Modulation (LFM) signal width 20MHz, f0 = 208e6; % Center frequency 208MHZ Fs = 96e6; % Sampling frequency 96MHZ Ts = 1/Fs; % Sampling interval K = B/Tp; % Frequency modulation slope PulseNumber=32; % number of emission pulses %c=3.0e8; %Speed of light (m/s)%Rf = 3.140e9/2; % Radar RF % Lambda = c/Rf; % Radar working wavelength %% Single pulse emission LFM signal t = -Tp/2:Ts:Tp/2; s_LFM=[exp(j*(2*pi*f0*t+pi*K*t.^2)),zeros(1,(T-Tp)/Ts)]; % The length of the finite sequence is equal to the total number of sampling points, M = T/Ts. subplot(2,1,1); plot(-Tp/2:Ts:T-Tp/2,real(s_LFM),'b','LineWidth',0.5); xlabel('t/s'); Title: Linear Frequency Modulation Signal Time-Domain Waveform grid on; axis tight; subplot(2,1,2); N=T/Ts+1; %N-point DFT transformation, N >= M finite length sequence length F_LFM = fft(s_LFM, N); freq=linspace(0,Fs,N); % Set the sampling frequency plot(freq*1e-6,abs(F_LFM),'b','LineWidth',0.5); xlabel('Frequency / MHz'); title('Linear Frequency Modulation Signal Frequency Domain Waveform'); grid on; axis tight; %% emitting a pulse train signal TotalNumber=SampleNumber*PulseNumber; SignalAll=zeros(1,TotalNumber+1); % All pulse signals, first fill with 0; number = fix(Tp * Fs); t1=linspace(0,T*PulseNumber,TotalNumber+1); SignalTemp=zeros(1,SampleNumber); % A pulse SignalTemp=s_LFM; % A single target in a pulse (without Doppler velocity) Signal = zeros(1, TotalNumber); SignalTemp=zeros(1,SampleNumber); % A pulse SignalTemp(1:N)=s_LFM; % A single pulse target (without Doppler velocity) Signal = zeros(1, TotalNumber); for i=1:PulseNumber      Signal((i-1)*SampleNumber+1:i*SampleNumber+1)=SignalTemp; endSignalAll=SignalAll+Signal; figure(2); subplot(2,1,1); plot(t1,real(SignalAll)); xlabel('t/s'); title('Transmit signal time domain waveform'); MATLAB simulation results
End

## Images

![Pulse-modulated LFM radar signal velocity and range measurement [with MATLAB code]](01.jpg)
![Pulse-modulated LFM radar signal velocity and range measurement [with MATLAB code]](02.jpg)

<!-- PAYMENT_BLOCK -->

## Get this dataset

- Payment link (Stripe): [Buy now](https://buy.stripe.com/3cs8yP7sY87d0vu9AB)
- Payment QR code: ![Payment QR code](pay.png)

<!-- /PAYMENT_BLOCK -->
