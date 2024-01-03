---
aliases:
- differentiation
- differentiation results
---

>[!statement]
>$$ \frac{d \ln{x}}{dx} = \frac{1}{x}$$
>>[!proof]-
>> $$\begin{align} 
>> \frac{d}{dx}\ln{x} &= \lim_{h\to0}\frac{\ln{\left(x+h\right)}-\ln{\left(x\right)}}{h} \\
>> 				   &= \lim_{h\to0}\frac{\ln{\left(\dfrac{x+h}{x}\right)}}{h} \\
>> 				   &= \lim_{h\to0}\frac{\ln{\left(1+\dfrac{h}{x}\right)}}{h} \\
>> 				   &= \lim_{h\to0}\frac1{h} \; \ln{\left(1+\dfrac{h}{x}\right)} \\
>> 				   &= \lim_{h\to0}\ln{\left(\left(1+\dfrac{h}{x}\right)^{\dfrac{1}{h}}\right)}
>> \end{align}$$
>> Let 
>> $$ \begin{align}
>>	n &= \frac{h}{x} \\
>>	nx &= h
>> \end{align}$$
>> Then
>>  $$\begin{align} 
>> \lim_{h\to0}\ln{\left(\left(1+\dfrac{h}{x}\right)^{\dfrac{1}{h}}\right)}  &= \lim_{n\to0}\ln{\left(\left(1+\dfrac{nx}{x}\right)^{\dfrac{1}{nx}}\right)}   \\ 
>> &= \frac{1}{x}\lim_{n\to0}\ln{\left(\left(1+n\right)^{\frac{1}{n}}\right)}   \\ 
>> &= \frac{1}{x}\ln{\left(\underbrace{\lim_{n\to0}\left(1+n\right)^{\frac{1}{n}}}_{=e}\right)}   \\ 
>> &= \frac{1}{x}\underbrace{\ln{\left(e\right)}}_{=1}   \\ 
>> &= \frac{1}{x}   \tag*{$\square$} 
>> 				   
>> \end{align}$$
>^dernatlog