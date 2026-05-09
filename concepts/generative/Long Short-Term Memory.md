Created : 2025-12-06 16:11
Tags :
Type :

---
# Long Short-Term Memory
LSTM or Long Short-Term Memory uses a memory cell for modelling long-range dependencies to avoid vanishing gradient

LSTM Cell :
![[Pasted image 20251206162532.png]]

Anatomy -
- **Forget Gate, $f$**
	- Controls which information is remembered, and which is forgotten; plus it can reset the cell state.
	- $$f_t = \sigma(\mathbf{W}_{fx}\mathbf{x}^{\langle t \rangle} + \mathbf{W}_{fh}\mathbf{h}^{\langle t-1 \rangle} + \mathbf{b}_f)$$

- **Input Gate, $i$** (sometimes denoted as $g$)
	- Controls which new information is stored in the cell state.
	- $$i_t = \sigma(\mathbf{W}_{ix}\mathbf{x}^{\langle t \rangle} + \mathbf{W}_{ih}\mathbf{h}^{\langle t-1 \rangle} + \mathbf{b}_i)$$

- **Candidate Cell State, $\tilde{c}$**
	- A vector of new candidate values (created by a tanh layer) that could be added to the state.
	- $$\tilde{c}^{\langle t \rangle} = \tanh(\mathbf{W}_{cx}\mathbf{x}^{\langle t \rangle} + \mathbf{W}_{ch}\mathbf{h}^{\langle t-1 \rangle} + \mathbf{b}_c)$$

- **Cell State Update, $c$**
	- Updates the old cell state $c^{\langle t-1 \rangle}$ into the new cell state $c^{\langle t \rangle}$. We multiply the old state by $f_t$ (forgetting things) and add the new candidate values scaled by $i_t$.
	- $$c^{\langle t \rangle} = f_t \odot c^{\langle t-1 \rangle} + i_t \odot \tilde{c}^{\langle t \rangle}$$
	- *(Note: $\odot$ denotes element-wise multiplication)*

- **Output Gate, $o$**
	- Controls which parts of the cell state are output to the hidden state.
	- $$o_t = \sigma(\mathbf{W}_{ox}\mathbf{x}^{\langle t \rangle} + \mathbf{W}_{oh}\mathbf{h}^{\langle t-1 \rangle} + \mathbf{b}_o)$$

- **Hidden State Output, $h$**
	- The final filtered output based on the cell state and the output gate.
	- $$\mathbf{h}^{\langle t \rangle} = o_t \odot \tanh(c^{\langle t \rangle})$$



So this would fit into an Multi-Layer RNN right here, replacing the hidden state :
![[Pasted image 20251206170744.png]]

So everything would plug-in as usual following the notations except for those in $C$ , which is the Cell State.











---
# References


