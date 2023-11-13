Definition
$$
\begin{split}
\mathcal{I}(\mathbf{r};\theta) := & \  \mathbb{E}_{\mathbf{r' \in \mathcal{D}(\mathbf{r})}}\Big[ \Big( \frac{\partial}{\partial \theta} \log p(\mathbf{r};\theta)\Big)^2 \  \Big\lvert \ \theta\ \Big] \\
= & \ \int_{\mathcal{D}(\mathbf{r})}{\Big( \frac{\partial}{\partial \theta} \log p(\mathbf{r};\theta)\Big)^2} p(\mathbf{r};\theta) \ d^{\dim{\mathbf{r}}}{\mathbf{r}}
\end{split}
$$
where the likelihood function is called [score](score%20%28Fisher%20Information%29). And generally Fisher information defines [[variance]] on [score](score%20%28Fisher%20Information%29).