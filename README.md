# LSHADE_RSP
基于jSO加入RSP机制，进一步提升收敛能力。V. Stanovov, S. Akhmedova and E. Semenkin, "LSHADE Algorithm with Rank-Based Selective Pressure Strategy for Solving CEC 2017 Benchmark Problems," 2018 IEEE Congress on Evolutionary Computation (CEC), Rio de Janeiro, Brazil, 2018, pp. 1-8, doi: 10.1109/CEC.2018.8477977.

# RSP策略
LSHADE-RSP基于jSO算法加入RSP机制，因此对RSP机制的实现和优势进行说明即可。
RSP策略全称基于排位选择压力策略，主要针对变异策略中作为探索部分的r1和r2。

公式：(1) Rank[i] = k * (N - i) + 1;
(2) pr[i] = Rank[i] / (Rank[1] + Rank[2] + ... + Rank[N])

其中范围[1,N]为适应度排名，因此排位机制就是根据适应度排名赋予每个个体一个选择概率，排名越高意味着个体有更高的概率被选中参与差分进化。

tips：很显然，在作者的意图中r1和r2都参与RSP机制，这意味着在论文中作者并没有用到存档机制。但是在作者开源的源码中LSHADE-RSP中r2并没有使用RSP机制，而是在种群和存档的集合中随机选取。
但是我依旧遵循论文要求将r1和r2都参与RSP机制，在实际测试中发现，算法的收敛能力得到提升，但是容易陷入局部最优，算是一种取舍。

other：贪婪系数p改为0.085-0.17。
