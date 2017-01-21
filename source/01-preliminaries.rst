.. role:: math(raw)
   :format: html latex
..

预备知识
========

1. 导论
-------

在进一步学习课程之前，本讲提供一些基础的“预备知识”。宏观经济学既是动态的，又是随机的。动态意味着我们必须时时追踪变量随时间的变化，而随机则意味着我们需要研究预期。因此，本讲将首先介绍一下符号系统及有关预期运算规则。接下来我们将介绍在宏观经济学中用到的随机过程—马尔可夫（
Markov
）过程及ARMA过程。然后我们讨论几个分析工具，这些工具将会在ARMA模型的框架中讨论，但是这些工具会有更广泛的应用，当我们学习经济模型时将会用到它们，如脉冲响应函数及方差分解等。我还将简要讨论一下关于“滤波”的基础知识。滤波是非常重要的，（因为存在趋势问题，）我们只有先把真实世界的数据转换后才能在经济模型的框架内开展分析。本讲最后将介绍卢卡斯批评（Lucas
Critique），卢卡斯批评奠定了现代宏观经济学的基础。

--------------

2. 符号系统与预期
-----------------

变量是某些可以（确定性地或随机地）改变的事物的实现。内生变量是指在模型“内部”决定的变量（即在均衡框架内根据决策规则通过优化问题推导出来的）。外生变量则是由模型“外部”决定的，通常是做为给定的因素。我们根据既定的外生变量，将其代入到模型中，模型运行的结果就是内生变量的实现。参数则是规制模型关系的数值（例如效用函数的曲度如何，决策行为人对未来效用流的折现倾向有多大，等等）。参数通常也被看作是外生且固定的，当然，模型中也可以设定参数为随机改变的，此时参数就变成是外生变量。我将采用拉丁字母（如
:math:`\(X\)` ，\ :math:`\(Y\)`\ ）来表示变量，而用希腊字母（如
:math:`\(\alpha, \beta\)`
）表示参数。我会尽量做到，只是可能偶尔会有些例外。

在描述宏观经济模型的变量时，我们还会遇到“状态”变量和“控制”变量两个术语。外生变量总是状态变量，但是内生变量则既可能是控制变量，也可能是状态变量。大致说来，“控制”变量是指其变量值是在模型中选择的，可以自由“跳跃”以响应新信息。状态变量的变量值则是行为人做决策时所需要的给定值。这些变量即可能是外生的（如一个最常用的术语，政府支出），也可能是内生的（资本存量、资产存量等）。状态变量是根据不同的控制变量要求而预先确定的：为了选择控制变量，需要预先知道状态变量。说到有些状态变量是内生的，是如下意义上的，即行为人当前的行为决策可能会影响未来状态变量的值，但是状态变量的当前值通常是已知的。

宏观经济模型和数据是动态的—我们在某时间点上观测变量的实现值。大多数宏观模型的时间是离散的（某些增长模型和资产定价模型例外）。令
:math:`\(X_t\)`\ 代表变量（可以是内生的也可以是外生的，可以是控制变量也可以是状态变量）。这个符号表示变量在是时间
:math:`\(t\)`\ 的变量实现值。\ :math:`\(X_{t-1}\)`\ 则代表在\ :math:`\(t\)`\ 之前的一期变量实现值。\ :math:`\(X_{t+k}\)`
代表在\ :math:`\(t\)`\ 时期之后第\ :math:`\(k\)`\ 期的变量实现值，依此类推。人们在使用时间标记符号时常常会有些翻来覆去的不一致情况，我也有这种情况（抱歉）。有时候，我们把时期0做为“现在”，然后向前推进时间；则在
:math:`\(t=0,1,2,...\)`\ 时的\ :math:`\(X_t\)`\ 代表的是当前（时期0）和今后的变量的实现值。在名外一些时候，我们用时期
:math:`\(t\)`
来代表现在，如此一来，就只能用\ :math:`\(X_{t+k}\)`\ 来代表时间向后（
:math:`\(k>0\)` ）或向前（ :math:`\(k<0\)` ）推进了。


宏观经济模型是随机的，即变量的实现值具有随机性。宏观模型的随机性本质源于外生变量，我们在建模时通常是将外生变量赋予随机性。由于模型是随机的，且行为人是前瞻性的，因此我们需要考虑预期问题。用\ :math:`\(E(X_t)\)`\ 代表\ :math:`\(X_t\)`\ 的无条件预期。所谓无条件是指行为人对系统的现状一无所知。
:math:`\(E_tX_{t+k}\)`\ 代表对\ :math:`\(X\)`\ 的未来实现值的基于在时间\ :math:`\(t\)`
所能获取的全部信息所做出的\ *条件*\ 预期。习惯上我们有\ :math:`\(E_tX_t = X_t\)`
，这是因为\ :math:`\(X_t\)` 在时期 :math:`\(t\)`
是已知的，其实现值已经没有不确定性。同理，我们还有
:math:`\(E_tX_{t−k} = X_{t−k}\)`.

对于两个任意的随机变量 :math:`\(Y\)` and
:math:`\(Z\)`\ ，根据迭代期望法则，
:math:`\(E(Y ) =E(E(Y | Z))\)`\ 。用文字表达的意思是，条件期望的无条件期望是无条件期望。
对于时间序列其含义如下：\ :math:`\( E_t(E_{t+1}(X_{t+2})) =E_tX_{t+2}\)`\ 。
再用文字表达的意思是，根据今天建立在对明天信息的条件猜想之上对今后两期的变量的条件猜想，恰恰就是基于今天的信息所能做出的最好猜想。（In
other words, your best guess conditional on today’s information of your
best guess conditional on tomorrow’s information of a variable two
periods out from now is just your best guess based on today’s
information.）

理性预期超出了简单的期望值的概念，对预期施加了更多结构性要求，这个领域的贡献要追溯到
Muth 和 Lucas。理性预期告诉我们，相关变量的未来实现值的期望
(i)在平均意义上是正确的； (ii)
在给定信息条件下，预测误差是不可预料的。换句话说，行为人只有在如下意义上才能建模出一致性的预期：（i）他们了解能够产生内生变量的模型并（ii）运用这些信息做出预测。这并不意味着行为人的预测不会出错。令
:math:`\(E_tX_{t+k}\)`
表示在时间\ :math:`\(t\)`\ 根据可用信息做出的此后第\ :math:`\(k\)`\ 期的\ :math:`\(X_t\)`\ 的条件预测。预测误差是\ :math:`\(u_{t+k} = X_{t+k} − E_tX_{t+k}\)`\ ：即实现值减去期望值。一般情况下\ :math:`\(u_{t+k} \)`\ 不会为零，但从平均意义上讲它应该为零，即它的无条件期望应该为零，\ :math:`\(E（u_{t+k}） =0\)`\ 。这背后的逻辑非常简单：如果我们在平均意义上有了预测误差，就无法形成最优的预期。进一步说，预测误差与做出预测时所有已知信息的协方差应该为零，\ :math:`\(\text{cov}（u_{t+k}, Z_t） =0\)`\ ，此处\ :math:`\(Z_t\)`\ 代表在\ :math:`\t\)`\ 时期任意已知的信息。ents
anything known at t. So rational expectations says that your forecasts
are right on average and are unpredictable. Another way to think about
this is that expectations are “optimal” in some sense – if you were
wrong on average or predictably wrong (and being wrong mattered), you
couldn’t be forming expectations optimally. Rational expectations is
widely used in empirical work, in that it implies restrictions that can
be used in econometrics. Note that rational expectation does not
necessarily rule out informational frictions: we could restrict the
information that agents have available to them. This may give rise to
them appearing to violate rational expectations (their forecast errors
are predictable), but only if one conditions on more information than
the agents have at the time they make the forecast.

--------------

3 随机过程
----------

如上所述，大部分宏观模型都是由对外生变量冲击过程所驱动的。我们需要明确这些外生状态变量所遵循的随机过程的性质。

The two most common ways to model a stochastic process are as a Markov
process (discreetoutcomes) or as an autoregressive moving average (ARMA)
process. The so-called “Markov Prop-erty” says that the current state of
a system is a sufficient statistic to forecast future values of
thestate; e.g. once you know St (the current state), knowing St−k for k
> 0 doesn’t tell you anythingabout the expected evolution of the state
going forward.

Let S ̄ be a N × 1 vector of possible realizations of some exogenous
state, call it st. Let P be aN × N probability (or transition) matrix.
Its elements are the the probabilities of transition fromstate i to
state j between periods t and t + 1. Hence:
