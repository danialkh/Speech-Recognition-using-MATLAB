function Voice_Rec(~)

x = audioread('three.wav');
%
% tag wave information 
%
voice=cov(x);
%

y0=audioread('Audio/denied.wav'); 	%'denied.wav' was used here as reference
y1=audioread('Audio/one.wav');
y2=audioread('Audio/two.wav');
y3=audioread('Audio/three.wav');
y4=audioread('Audio/four.wav');
y5=audioread('Audio/five.wav');

h=audioread('Audio/allow.wav');


ref=cov(y0);
delta0 = abs(ref - voice);
sel = ref;
dif = abs(delta0);
 
% all allowed wave files must be loaded and compared 
% to the input, one at a time
%
one=cov(y1);
delta1 = abs(one - voice);
if (delta1 <= dif) 
    sel = one;
    dif = abs(delta1);
end
  
two = cov(y2);
delta2 = abs(two - voice);
if (delta2 <= dif) 
    sel = two;
    dif = abs(delta2);
end 
     
three = cov(y3);
delta3 = abs(three - voice);
if (abs(delta3) <= dif) 
    sel = three;
    dif = abs(delta3);
end
 
four = cov(y4);
delta4 = abs(four - voice);
if (delta4 <= dif) 
    sel = four;
    dif = abs(delta4);
end 
 
five = cov(y5);
delta5 = abs(five - voice);
if (delta5 <= dif) 
    sel = five;
    dif = abs(delta5);
end
 
 
if sel == one
	fprintf("one");
elseif sel == two
	fprintf("two");
elseif sel == three
	fprintf("three");
elseif sel == four
	fprintf("four");
elseif sel == five
	fprintf("five");
else
	fprintf("not find");
   
end
