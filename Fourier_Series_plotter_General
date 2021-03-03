#General 
#Fourier

#This is a plotting tool for any periodic Fourier series, when run you can input your period 
#  P, a_0, a_n, and b_n Coefficients, then use the slider to increase the maximum number in
#  the summation and display the wave form.


import numpy as np
import matplotlib.pyplot as plt
from matplotlib.widgets import TextBox,Slider ,Button
from numpy import pi,sin,cos 

fig, ax = plt.subplots()
fig.subplots_adjust(bottom=0.4)
plt.axvline(x=0, color='black') 
plt.axhline(y=0, color='black') 
x = np.linspace(-10,10,num = 1000 )
plt.style.use('classic')
plt.title('Fourier plotter for any periodic function ')

T = '4' 
a0 = '1'
y = eval(a0)/2
itt = '2'
an = "((-1)**n)/n"
bn = "0"
for n in range(1,int(itt)):
    ann = eval(an)
    bnn = eval(bn)
    y = y + ann*cos((2*pi*n*x)/eval(T)) + bnn*sin((2*pi*n*x)/eval(T))

aln=[an]
bln=[bn]     
alo=[a0] 
Ts=[T]
nitt=[itt]
l, =  plt.plot(x,y,'r-')
plt.xlabel('$x$')
plt.ylabel('$f(x)$')

colour = (0.75,0.75,0.75,1)

box2 = plt.axes([0.3,0.21,0.2,0.04]) 
but3 = Button(box2, '', color='w',hovercolor = 'w') 
box3 = plt.axes([0.3,0.25,0.2,0.04],xlabel = 'n = '+str(itt)) 
but4 = Button(box3, 'Summed up to: ', color='w',hovercolor = 'w') 

box = plt.axes([0.50,0.2,0.4,0.1]) 
but = Button(box, r'$f\:(x) = \frac{a_0}{2} + \sum_{n = 1}^{\infty} \: a_n\cos(\frac{2\pi nx}{P}) + b_n\sin(\frac{2\pi nx}{P})$', color='w',hovercolor = 'w')

axR = plt.axes([0.20, 0.025, 0.5, 0.03], facecolor=colour)
sR = Slider(axR, 'Number of \nItterations', 2, 1000, valinit=1 , valstep=1,color='blue')

def update(val):
    itt = sR.val
    nitt.append(itt)
    anns = aln[len(aln)-1]
    bn = bln[len(bln)-1]
    a0 = eval(alo[len(alo)-1]) 
    y = a0/2
    T = Ts[len(Ts)-1]
    for n in range(1,int(itt)):
        ann = eval(anns)
        bnn = eval(bn)
        y = y + ann*cos((2*pi*n*x)/eval(T)) + bnn*sin((2*pi*n*x)/eval(T)) 
    box3.set_xlabel('n = '+str(itt))
    l.set_ydata(y)
    ax.relim()
    ax.autoscale_view()
    plt.draw()    


sR.on_changed(update)

def submit(expression):
    aln.append(expression)
    a0 = eval(alo[len(alo)-1])
    y = a0/2
    itt = int(eval(nitt[len(nitt)-1]))
    bn = bln[len(bln)-1]
    T = Ts[len(Ts)-1]
    for n in range(1,int(itt)):
        ann = eval(expression)
        bnn = eval(bn)
        y = y + ann*cos((2*pi*n*x)/eval(T)) + bnn*sin((2*pi*n*x)/eval(T)) 
    l.set_ydata(y)
    ax.relim()
    ax.autoscale_view()
    plt.draw() 
    
def submit2(expression):
    bln.append(expression)
    a0 = eval(alo[len(alo)-1])
    y = a0/2
    itt = int(eval(nitt[len(nitt)-1]))
    T = Ts[len(Ts)-1]
    anns = aln[len(aln)-1]
    for n in range(1,int(itt)):
        ann = eval(anns)
        bnn = eval(expression)
        y = y + ann*cos((2*pi*n*x)/eval(T)) + bnn*sin((2*pi*n*x)/eval(T)) 
    l.set_ydata(y)
    ax.relim()
    ax.autoscale_view()
    plt.draw()

def submit3(expression):
    alo.append(expression)
    a0 = eval(expression)
    y = a0/2
    itt = int(eval(nitt[len(nitt)-1]))
    T = Ts[len(Ts)-1]
    anns = aln[len(aln)-1]
    bn = bln[len(bln)-1]
    for n in range(1,int(itt)):
        ann = eval(anns)
        bnn = eval(bn)
        y = y + ann*cos((2*pi*n*x)/eval(T)) + bnn*sin((2*pi*n*x)/eval(T)) 
    l.set_ydata(y)
    ax.relim()
    ax.autoscale_view()
    plt.draw()
    
def submit4(expression):
    Ts.append(expression)
    T = expression
    a0 = eval(alo[len(alo)-1])
    y = a0/2
    itt = int(eval(nitt[len(nitt)-1]))   
    anns = aln[len(aln)-1]
    bn = bln[len(bln)-1]
    for n in range(1,int(itt)):
        ann = eval(anns)
        bnn = eval(bn)
        y = y + ann*cos((2*pi*n*x)/eval(T)) + bnn*sin((2*pi*n*x)/eval(T)) 
    l.set_ydata(y)
    ax.relim()
    ax.autoscale_view()
    plt.draw()
    
    
    
axbox4 = fig.add_axes([0.1, 0.22, 0.2, 0.055],xlabel = '$P$')
text_box4 = TextBox(axbox4,"")
text_box4.on_submit(submit4)
text_box4.set_val("2") 

axbox3 = fig.add_axes([0.1, 0.1225, 0.2, 0.055],xlabel = '$a_o$')
text_box3 = TextBox(axbox3,"")
text_box3.on_submit(submit3)
text_box3.set_val("4") 

axbox = fig.add_axes([0.3, 0.1225, 0.3, 0.055],xlabel = '$a_n$')
text_box = TextBox(axbox,"")
text_box.on_submit(submit)
text_box.set_val("0")  

axbox2 = fig.add_axes([0.6, 0.1225, 0.3, 0.055],xlabel = '$b_n$')
text_box2 = TextBox(axbox2,"")
text_box2.on_submit(submit2)
text_box2.set_val("((-1)**n)/n")
ax.grid()
plt.show()






