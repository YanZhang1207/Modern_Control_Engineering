# Matlab语法

## 波特图
### 传输函数形式
绘制传输函数$G(s)=\frac{25}{s^2+4s+25}$的波特图
```
num = [25]; 
%定义传输函数分子中s幂次项前的系数

den = [1 4 25]; 
%定义传输函数分母中s幂次项前的系数

w = logspace(-2,3,100);
%定义绘制波特图的角频率范围$10^{-2}-10^{3}$，在该范围内包括起点和终点共$100$个数据点

bode(num,den,w) 
%根据给定的角频率范围绘制波特图

[mag,phase,w] = bode(num,den,w)
%根据给定的角频率范围以矩阵形式输出幅值和相位差情况

mag = mag(:);
phase = phase(:);
w = w(:);
% 将mag、phase和w从数组转换为向量

magdB = 20*log10(mag)
%幅值向量转换为dB形式向量

bode_table = table(w, mag, magdB, phase, ...
    'VariableNames', {'Frequency_rad_s', 'Magnitude', 'Magnitude_dB', 'Phase_degrees'});
%创建数据表格

disp('Bode Diagram Data Table:');
disp(bode_table(1:10, :)); 
% 只显示前10行

title('Bode Diagram of G(s) = 25/(s^2 + 4s + 25)')
%绘图命名
```

### 状态空间形式