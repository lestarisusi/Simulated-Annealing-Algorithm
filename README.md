# Simulated-Annealing-Algorithm
Simulated Annealing is a kind of probabilistic global optimization techniques based on natural phenomena, which is inspired by physical process of annealing. This Algorithm is written in Octave.
function []=SimulatedAnnealing(i,T,eps,r)

%%Plot of function%%
x=-4:0.1:4;
y=-4:0.1:4;
[x,y]=meshgrid(x,y);
z=0.5*x.^4-0.5*16*x.^2+0.5*5*x.+0.5*y.^4-0.5*16*y.^2+0.5*5*y.^1;
surf(x,y,z)

%Simulated Annealing%
i0=-4+(4-(-4))*rand(2,1);%Generate state i (initial state)
i=i0;
T=100; %initial temperature
eps=0.5; %neighbourhood radius of i
r=0.95; %temperature cooling rate
N=100; %Maximum iterations
E=20; %Epoch length
%The purpose is to minimize f%
for iter=0:N
  for k=0:E
      j=(i-eps)+rand(2,1)*2*eps; %random neighbour of i
      %for example we would minimize f
      f=(i(1)^4-16*i(1)^2+5*i(1))/2+(i(2)^4-16*i(2)^2+5*i(2))/2;
      g=(j(1)^4-16*j(1)^2+5*j(1))/2+(j(2)^4-16*j(2)^2+5*j(2))/2;
      
      d=g-f;
      if d<0
         i=j;
      else if rand()<e^(-d/T)
         i=j;
      endif
      endif
  endfor
  T=r*T;
endfor
      disp('Initial approximation:'); disp(i0);
      disp('Minimum value:'); disp(f);
      disp('at point: '); disp(i);
endfunction
