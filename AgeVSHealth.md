# TheDI
This project is for The Data Incubator program (October 2017). The data analyzed was downloaded from the Substance Abuse and Mental Health Archive titled National Survey on Drug Use and Health 2015 (NSDUH-2015-DS0001). The following code is a Matlab function which generates  graphs to show the correlation between depression and the age of first drug use for 9 different drugs.  

function [ ] = AgeVSHealth

Cig = [224, 3501, 411, 33, 5, 0, 0, 0, 4174, 1834; 763, 18549, 2884, 179, 33, 4, 2, 0, 22414, 14641];

CigR = RDU(Cig);

Mar = [54, 3136, 536, 43, 15, 7, 0, 0, 3791, 2230; 151, 14122, 3298, 313, 87, 29, 10, 8, 18018, 19116];  

MarR = RDU(Mar);

Alc = [194, 4234, 788, 30, 7, 3, 0, 0, 5256, 740; 594, 24104, 6721, 282, 71, 13, 8, 1, 31794, 5115];

AlcR = RDU(Alc);

Coc = [2, 795, 470, 74, 8, 4, 0, 0, 1353, 4670; 9, 2374, 2467, 292, 50, 6, 0, 0, 5198, 32010];

CocR = RDU(Coc);

Her = [0, 122, 137, 40, 4, 4, 0, 0, 307, 5724; 2, 219, 303, 69, 17, 3, 0, 0, 613, 36629];

HerR = RDU(Her);

Hal = [3, 1156, 410, 38, 4, 0, 1, 0, 1612, 4400; 22, 3991, 2081, 153, 24, 5, 2, 0, 6278, 30868]; 

HalR = RDU(Hal);

Crk = [0, 189, 155, 55, 18, 5, 0, 0, 422, 5608; 2, 370, 531, 174, 46, 10, 0, 0, 1133, 36106];

CrkR = RDU(Crk);

Meth = [1, 341, 204, 63, 18, 1, 0, 0, 628, 5398; 6, 982, 745, 139, 33, 5, 1, 0, 1911, 35309];

MethR = RDU(Meth);

Oxi = [1, 86, 66, 14, 11, 3, 1, 0, 182, 4591; 0, 118, 93, 24, 14, 4, 1, 0, 254, 32986];

OxiR = RDU(Oxi);

figure (1)

plot([0:10:70],Cig(1,1:8), '-*c')

axis([0 70 0  4500])

title('The correlation between age of first drug use and depression.')

xlabel('Range of Age (0=0-9, 1=10-19, etc)')

ylabel('Number of People Reported Depressed (who have used drugs)')

hold on

plot([0:10:70],Mar(1,1:8), '-*y')

plot([0:10:70],Alc(1,1:8), '-*m')

plot([0:10:70],Coc(1,1:8), '-*r')

plot([0:10:70],Her(1,1:8), '-*g')

plot([0:10:70],Meth(1,1:8), '-*k')

plot([0:10:70],Oxi(1,1:8), '-*b')

legend('Cigarettes','Marijuana','Alcohol','Cocaine','Heroin','Meth','Oxycontin')

hold off

figure (2)  

plot([0:10:70],CigR(1,1:8), '-*c')

axis([0 70 0  100])

title('The correlation between age of first drug use and depression (relative).')

xlabel('Range of Age (0=0-9, 1=10-19, etc)')

ylabel('Percent People Reported Depressed (who have used drugs)')

hold on

plot([0:10:70],MarR(1,1:8), '-*y')

plot([0:10:70],AlcR(1,1:8), '-*m')

plot([0:10:70],CocR(1,1:8), '-*r')

plot([0:10:70],HerR(1,1:8), '-*g')

plot([0:10:70],MethR(1,1:8), '-*k')

plot([0:10:70],OxiR(1,1:8), '-*b')

legend('Cigarettes','Marijuana','Alcohol','Cocaine','Heroin','Meth','Oxycontin')

hold off

end

function [v] = RDU(w)

%function to compute relative drug use

v = w(1,1:8)./(w(1,1:8)+w(2,1:8));

k = find(isnan(v));

v(1,k) = 0;

v = v*100;

end
