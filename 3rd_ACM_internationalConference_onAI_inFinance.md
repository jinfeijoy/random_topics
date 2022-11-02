* Learning Financial Graphs
  * **Heavy Tail** most of financial data is not gaussian distribution, and they are heavy-tailed. The heavy-tailed formulation is nonconvex and difficult to solve directly.
    * instead, we can employ the [majorization-minimization (MM) framework](https://palomar.home.ece.ust.hk/papers/2017/SunBabuPalomar-TSP2017%20-%20MM.pdf) to iteratively solve the graph problem ([M. Cardoso et al., 2021](https://palomar.home.ece.ust.hk/papers/2022/CardosoYingPalomar-ElsevierBook2022.pdf))
    * k-component heavy-tailed graph
    * data normalization need to be done before data feed into GMRFgraph learning framework
    * the heavy-tailed MRF is naturally sparse and more interpretable 
    * the propsed k-component heavy-tailed MRF does not show isolated nodes, is more sparse and produces a more interpretable graph
    * the proposed k-component bipartite heavy-tailed MRF does not show isolated nodes and has a better accuracy
  * Summary:
    * unfortunately, for financial data, most of the existing method are not appropriate. 
    * The most promising formulations seem to revolve around the heavy-tailed MRF; in particular:
      * vanilla heavy-tailed MRF fomulation
      * k-component heavy-tailed MRF formulation
      * bipartite heavy-tailed MRF formulation
      * k-component bipartite heavy-tailed MRF formulation   
    * Presenter link:
      * https://www.danielppalomar.com/
      * https://github.com/dppalomar
      * https://www.youtube.com/c/danielpalomar/videos     

* Network Representations for Financial System Modelling
* Network Effects in limit order book analysis and covariance estimation
* 
