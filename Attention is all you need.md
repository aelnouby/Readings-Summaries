#### Paper: https://arxiv.org/pdf/1706.03762.pdf

- Introduction

  Previous methods usually use RNNs or causal convs for sequence to sequence modeling, usually with an attention mechansim that ties the decoder to the encoder. In this paper, the authors propose a new pardigm of using attention only networks. The new archtiecture is more parallelizable and with signficantly less parameters than previous methods, moreover it achieves state of the art results on the task of machine translation.

  Previuos methods relied on recurrent units (RNNs, LSTMs, GRUs), recurrent units are sequential by nature as every new generation need to look at the previous hidden state from previous generations, this prevents good parallelization, additionaly, as sequences get longer we start having problems with long term depenencies with the famous vanishing gradient problems. Attention mechanism provides a good solution to the second problem as it allows the decoder to ask the encoder from any previous time step about information, this is fast as it 2 large matrix multiply (dot product followed by softmax). 
  
  A good blog post explaining the paper: https://ricardokleinklein.github.io/2017/11/16/Attention-is-all-you-need.html
