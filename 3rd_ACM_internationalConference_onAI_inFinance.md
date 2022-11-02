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
  * Network representations for probabilistic modeling: 
    * Application: Covariance selection problem: estimate (sparse inverse) covariance that maximizes model likelihood
    * Application: systemic risk and stress propagation, mean conditional loss under stress ([1](https://www.mdpi.com/1911-8074/14/5/213),[2](https://iopscience.iop.org/article/10.1088/2632-072X/ac6721/meta) )
      * a single variables in central position is more impactful but, a group of central variables become less impactful on the rest of the system
      * roup of variables with highest impact stay in central positions but are not clustered together  
    * 
  * Causality: Wiener-Granger approach: X cause Y when the past of X provides extra contribution on the knowledge of the future of Y, causality as a conditional lagged dependency
    * Application: sentiment influencing prices
  * Higher order networks
    * Novel neural network architecture: use the higher order network structure of information filtering networks for a novel artificial neural network architecture
    * Application: regression competition  
* Network Effects in limit order book analysis and covariance estimation
  * [Cross impact](https://papers.ssrn.com/sol3/papers.cfm?abstract_id=3993561)
    *  use the past daily/weekly/monthly volatility (or correlation) as node features. We don't have any edge features. We mainly considered the binary graph
    *  what is cross impact: the price of a given asset might be moved by the orders of other assets
    *  use graphs as the mathematical model to represent two types of interdependence in the U.S. equity market: voatility , correlation
    *  Through graphs, are able to apply neighboarhood aggregation to generate a new input feature for every underlying asset and incorporate it into the traditional models for volatility/correlation forecasting.
    *  neighboarhood aggregation is an effective method to integrate the structural interdependence of all the node pairs into the features observed on every node while maintaining a low dimension.
    *  Graphical LASSO is a sparsity-penalized maximum likelihood estimator for the precision matrix. 
* Multimodel stock embeddings
  * generating context sets
    * Return data: using return data (return rate of stock) to pick context: most closed returns can be grouped as 1 group 
    * News data: mentioned in the same news article
    * Target: maximise similarity between context & true target embeddings:
      * aggregate the context embeddings (h = 1/C * sum(v) -- v is the embedding for asset a
      * compute similarity between h and each embedding by dot product 
      * normalize the similarities to a probability distribution
      * to maximize the probability for the true target stock we can minimise L
