# Forritnarverkefni
Forritunarverkefni 

slodi=uigetdir('Veldu moppu')

for i=1:33
    skra=strcat('SUB',num2str(i),'_closed','.xlsx');
    s=strcat(slodi,'\',skra);
    A(i).closed=xlsread(s);
end

for i=1:33
    skra=strcat('SUB',num2str(i),'_open','.xlsx');
    s=strcat(slodi,'\',skra);
    A(i).open=xlsread(s);
end

skra=strcat('Stimuli','.xlsx');
s=strcat(slodi,'\',skra);
B=xlsread(s);

Tidni=B(:,2)

for i=1:length(Tidni)
    if Tidni(i)==20
        Tidni(i)=0;
    elseif Tidni(i)==59
        Tidni(i)=1;
    end  
end
B(:,2)=Tidni;

%Í lið 2 breyttum við söfnunartíðninni 50 Hz í sekúndur og var það 1/50 sek sem er u.þ.b. 0.02 sek
%finnum núna fjölda stimula/örvana
x=find(B(:,2)==1);   %hérna er staðsetningin á örvunum
stnum=length(x);
