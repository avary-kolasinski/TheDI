# TheDI
This project is for The Data Incubator program (October 2017). The data analyzed was downloaded from the Substance Abuse and Mental Health Archive titled National Survey on Drug Use and Health 2015 (NSDUH-2015-DS0001). The following code is a Matlab function which generates  graphs to show the correlation between depression and the frequency drug use in the past month for 9 different drugs.  

function [ ] = FrequencyVSHealth

Cig = [369, 152, 129, 106, 133, 129, 1309, 2327, 1861, 1834; 1356, 611, 399, 342, 470, 502, 4594, 8274, 14284, 14641];

CigR = RDU(Cig);

Mar = [360, 151, 86, 81, 101, 129, 329, 1237, 2500, 2230; 1160, 463, 260, 234, 325, 473, 850, 3765, 14150, 19116];

MarR = RDU(Mar);

Alc = [1665, 656, 352, 237, 190, 129, 96, 3325, 1850, 740; 10419, 4319, 2254, 1323, 1294, 851, 557, 21017, 10552, 5115];

AlcR = RDU(Alc);

Coc = [91, 19, 11, 5, 3, 0, 4, 133, 1213, 4670; 181, 29, 14, 3, 2, 3, 3, 235, 4945, 32010];

CocR = RDU(Coc);

Her = [13, 6, 5, 2, 1, 4, 11, 42, 258, 5724; 8, 3, 5, 5, 5, 3, 10, 39, 564, 36629];

HerR = RDU(Her);

Hal = [94, 8, 1, 3, 0, 1, 1, 108, 1477, 4400; 197, 8, 6, 4, 2, 0, 2, 219, 6007, 30868];

HalR = RDU(Hal);

Crk = [20, 4, 6, 1, 2, 0, 1, 34, 390, 5608; 13, 7, 3, 1, 1, 1, 2, 28, 1101, 36106];

CrkR = RDU(Crk);

Meth = [23, 10, 7, 8, 10, 8, 8, 74, 554, 5398; 34, 8, 5, 1, 4, 8, 10, 70, 1844, 35309];

MethR = RDU(Meth);

Oxi = [160, 53, 25, 21, 21, 16, 23, 319, 1107, 4591; 292, 66, 40, 27, 18, 8, 20, 471, 3680, 32988];

OxiR = RDU(Oxi);

figure (1)          

plot([0, 1, 5, 10, 15, 20, 25, 30],[Cig(1,9),Cig(1,1:7)], '-*c')

axis([0 30 0  2500])

title('The correlation between frequency of drug use and depression.')

xlabel('Range of days used in past month (0=no days, 1=1-4 days, etc)')

ylabel('Number of People Reported Depressed (who have used drugs)')

hold on

plot([0, 1, 5, 10, 15, 20, 25, 30],[Mar(1,9),Mar(1,1:7)], '-*y')

plot([0, 1, 5, 10, 15, 20, 25, 30],[Alc(1,9),Alc(1,1:7)], '-*m')

plot([0, 1, 5, 10, 15, 20, 25, 30],[Coc(1,9),Coc(1,1:7)], '-*r')

plot([0, 1, 5, 10, 15, 20, 25, 30],[Her(1,9),Her(1,1:7)], '-*g')

plot([0, 1, 5, 10, 15, 20, 25, 30],[Meth(1,9),Meth(1,1:7)], '-*k')

plot([0, 1, 5, 10, 15, 20, 25, 30],[Oxi(1,9),Oxi(1,1:7)], '-*b')

legend('Cigarettes','Marijuana','Alcohol','Cocaine','Heroin','Meth','Oxycontin')

hold off

figure (2)          

plot([0, 1, 5, 10, 15, 20, 25, 30],CigR(1,1:8), '-*c')

axis([0 30 0  100])

title('The correlation between frequency of drug use and depression (relative).')

xlabel('Range of days used in past month (0=no days, 1=1-4 days, etc)')

ylabel('Percent of People Reported Depressed (who have used drugs)')

hold on

plot([0, 1, 5, 10, 15, 20, 25, 30],MarR(1,1:8), '-*y')

plot([0, 1, 5, 10, 15, 20, 25, 30],AlcR(1,1:8), '-*m')

plot([0, 1, 5, 10, 15, 20, 25, 30],CocR(1,1:8), '-*r')

plot([0, 1, 5, 10, 15, 20, 25, 30],HerR(1,1:8), '-*g')

plot([0, 1, 5, 10, 15, 20, 25, 30],MethR(1,1:8), '-*k')

plot([0, 1, 5, 10, 15, 20, 25, 30],OxiR(1,1:8), '-*b')

legend('Cigarettes','Marijuana','Alcohol','Cocaine','Heroin','Meth','Oxycontin')

hold off

end

function [v] = RDU(w)

v(1,1) = w(1,9)/(w(1,9)+w(2,9));

v(1,2:8) = w(1,1:7)./(w(1,1:7)+w(2,1:7));

k = find(isnan(v));

v(1,k) = 0;

v = v*100;

end

