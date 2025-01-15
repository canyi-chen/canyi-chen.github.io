@def title = "Selected Exercises for Markov Chain"
@def date = "04/12/2022"
@def tags = ["meta", "julia"]

# Selected Exercises for Markov Chain

12. A fair coin is tossed repeatedly and independently. Find the expected number of tosses till the pattern HTH appears.

**Solution.** Call HTH our target. Consider a chain that starts from a state called nothing $\emptyset$ and is eventually absorbed at HTH. If we first toss H then we move to state H because this is the first letter of our target. If we toss a T then we move back to $\emptyset$ having expended 1 unit of time. Being in state H we either move to a new state HT if we bring T and we are 1 step closer to the target or, if we bring H, we move back to H: we have expended 1 unit of time, but the new H can be the beginning of a target. When in state HT we either move to HTH and we are done or, if T occurs then we move to $\emptyset$. The transition diagram is

![](https://cdn.mathpix.com/snip/images/yZV76W5zxMrF7K2ssBfEXCb8VDo5iDg2vON9YLlJ_rs.original.fullsize.png)

Rename the states $\emptyset, \mathrm{H}, \mathrm{HT}, \mathrm{HTH}$ as $0,1,2,3$, respectively. Let $\psi(i)$ be the expected number of steps to reach HTH starting from $i$. We have
$$
\begin{aligned}
&\psi(2)=1+\frac{1}{2} \psi(0) \\
&\psi(1)=1+\frac{1}{2} \psi(1)+\frac{1}{2} \psi(2) \\
&\psi(0)=1+\frac{1}{2} \psi(0)+\frac{1}{2} \psi(1)
\end{aligned}
$$
We solve and find $\psi(0)=10$.