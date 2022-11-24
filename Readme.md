# A simple Mass-Spring system.



## **How to Build and Compile:**

```bash
cmake -Bbuild .
cd build
cmake --build . --parallel 8
```

## How to run:

```bash
cd bin/Debug
./Mass-Spring.exe
```



### 1. Math and physics theorem

base on the blog:

https://www.cnblogs.com/shushen/p/5473264.html

Kinematic formula:
$$
\frac{\mathrm{d} }{\mathrm{d}t } \binom{x}{\dot{x}} =\binom{v}{M^{-1}f(x,v)}\

\binom{\Delta x}{\Delta v} =h\binom{v_{0}+\Delta v}{M^{-1}f(x_0+\Delta x,v_0+\Delta v)} \
$$

$$
对f一阶泰勒展开：\\
f(x_0+\Delta x,v_0+\Delta v)=f_0+\frac{\partial f}{\partial x} \Delta x+\frac{\partial f}{\partial v} \Delta v\\
最终得到隐式欧拉方程：\\
(I-hM^{-1}\frac{\partial f}{\partial v}-h^{2}M^{-1}\frac{\partial f}{\partial x})\Delta v=hM^{-1}(f_0+h\frac{\partial f}{\partial x}v_0)
$$

physical modeling the mass-spring system:

![image-20221124145715515](C:\Users\RJ\Desktop\Mass-Spring\Readme.assets\image-20221124145715515.png)

the construct force  for the two masses i,j:

![image-20221124145824660](C:\Users\RJ\Desktop\Mass-Spring\Readme.assets\image-20221124145824660.png)

the damping force  for the two masses i,j:

![image-20221124145856731](C:\Users\RJ\Desktop\Mass-Spring\Readme.assets\image-20221124145856731.png)



### 2. My work

almost all codes are done by myself, and the main codes are in ./project/Mass-Spring. I have modeled the mass-spring system, written a simple function to load the obj data from ./media/obj , and constructed sparse matrix and solved it by conjugate gradient method written by myself. Some other codes are base on the computer-graphics course  frame but I have read all, and the Eigen lib just to use the matrix and vector data structure.



### 3. Result

you can use "w,s,a,d" to move the view, but it is a perspective camera so it may looks a bit strange.

![image-20221124151306387](C:\Users\RJ\Desktop\Mass-Spring\Readme.assets\image-20221124151306387.png)

Press the space to start the simulation progress, then it will output "1" to tell you the system is continue. But sometimes it stops, which needs you to press space again.

![QQ录屏20221124151438 00_00_00-00_00_30](C:\Users\RJ\Desktop\Mass-Spring\Readme.assets\QQ录屏20221124151438 00_00_00-00_00_30.gif)

you can change the mode with simply draw lines or draw with texture, but I am too lazy to only texture the lines...

what's more, you can change the wind force , time steps, stiffness of the springs by the bottom bar. the direction of the wind force is from outside the screen to inside the screen.