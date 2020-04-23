20200422

1.将排斥势加到了模拟的流程中</br>
具体的步骤为：将之前更新活性粒子的位置这一步进行修改，一是要引入粒子之间的排斥力。二是要将时间步长进行缩短。</br>
排斥力这里试了LJ势，发现程序很容易崩掉，所以先简单换成了一个与r平方反比的斥力。</br>
时间长取MPC每一大步更新时间的N分之一，然后更新N步即可。</br>

之前未加排斥势的结果如下：</br>
<div align=center>
 <img width="300" height="300" src="https://github.com/YiYiXia/SoftMatter/blob/master/20200422/2.gif">
</div>
</br>
加了排斥势的结果如下：</br>
<div align=center>
 <img width="300" height="300" src="https://github.com/YiYiXia/SoftMatter/blob/master/20200422/1.gif">
</div>
粒子之间的距离的确有所增加。

<div align=center>
 <img width="300" height="300" src="https://github.com/YiYiXia/SoftMatter/blob/master/20200422/3.gif">
</div>

<div align=center>
 <img width="300" height="300" src="https://github.com/YiYiXia/SoftMatter/blob/master/20200422/4.gif">
</div>

<div align=center>
 <img width="300" height="300" src="https://github.com/YiYiXia/SoftMatter/blob/master/20200422/5.gif">
</div>
