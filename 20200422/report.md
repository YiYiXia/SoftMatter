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
粒子之间的距离的确有所增加。</br>

2.模拟中的一个问题</br>
当只针对一定角度范围内的活性粒子做Vicsek处理时，活性粒子会形成聚团，像鱼群一样集体转圈。</br>
当没有加排斥势时，结果如下:</br>
<div align=center>
 <img width="300" height="300" src="https://github.com/YiYiXia/SoftMatter/blob/master/20200422/4.gif">
</div>
但是加了排斥势之后：</br>
<div align=center>
 <img width="300" height="300" src="https://github.com/YiYiXia/SoftMatter/blob/master/20200422/3.gif">
</div>
成团转圈的活性粒子会把流体粒子排出粒子团所在的区域。</br>
对于这一现象的成因，我的想法是，这就有点像用筷子持续搅动一杯水时，水由于离心作用，会向外侧跑，因此水的中间会出现空洞。</br>
对于二者之间差异的原因，我的想法是：</br>
当不加排斥势时，尽管一部分流体粒子会被甩出去，但是由于活性粒子所占据的空间较小，流体粒子甩出去之后会受周围其他流体粒子作用给"推"回去。所以不太容易形成空洞。</br>
当加了排斥势之后，由于活性粒子散开，占据的空间较大，所以，当流体粒子在一个cell里被甩进另一个cell里时，会被下一个cell继续甩出去。所以就造成空洞越来越大。</br>

为了不让空洞形成，就需要其他地方的流体给这部分流体提供向心力。我尝试了增加环境的温度，使得其他流体粒子的的随机涨落更大，让流体粒子更难被甩出去。结果如下：</br>
<div align=center>
 <img width="300" height="300" src="https://github.com/YiYiXia/SoftMatter/blob/master/20200422/5.gif">
</div>
从结果看，这的确能缓解一部分空洞的出现，但这也可能会有负面影响，即温度如果过高，活性粒子驱动力的作用效果似乎就会减弱。</br>
不知道还有什么其他办法可以解决空洞这个问题？
