# Blackjack AI: Monte Carlo, TD, and Q-Learning

This project is an AI-powered Blackjack engine where I implemented **Monte Carlo policy evaluation**, **Temporal-Difference learning**, and **Q-Learning** from scratch. The core idea is to train an agent that can learn to play Blackjack optimally through repeated simulations — no pre-programmed strategies, just reinforcement learning in action.  

The game engine is adapted from [this repo](https://github.com/ServePeak/Blackjack-Python/blob/master/blackjack.py), but all the learning logic was implemented by me.  

## 🃏 The Game
The project follows standard Blackjack rules with some simplifications for simulation speed. You can play manually with **Hit** and **Stand**, or let the AI take over with Monte Carlo (MC), Temporal-Difference (TD), or Q-Learning (QL).  

As the AI trains, it updates state values in the background. Watching them converge is a neat way to see learning in real-time. Once Q-Learning is implemented, the **AutoPlay** mode uses the learned Q-values to make decisions — and you can see the win rate improve toward ~41%.  

## Implemented Algorithms
- **Monte Carlo Policy Evaluation**  
  Learns state values by averaging rewards over many simulated games under a fixed policy.  
- **Temporal-Difference Policy Evaluation**  
  Updates state values incrementally after each step instead of waiting until the end of the episode.  
- **Q-Learning**  
  Learns action-value pairs with an ε-greedy exploration strategy. After enough training, the agent can play Blackjack competitively against the dealer.  

## Usage
Run the game with:
```bash
python main.py
```
Run deterministic tests:

```bash
Copy code
python main.py -t 1 -a 1
```
Run convergence tests:

```bash
Copy code
python main.py -t 2
```
In-game keyboard options:
- h: Hit
- s: Stand
- m: Toggle Monte Carlo learning
- t: Toggle TD learning
- q: Toggle Q-learning
- a: AutoPlay with the current AI
- 1: Save AI state
- 2: Load AI state

## Testing
Two built-in testers are included:
- 3-step deterministic test (-t 1) for quick debugging of MC and TD
- 1-million-step convergence test (-t 2) to verify long-term learning stability

## Blackjack Rules (Simplified)
- Goal: Beat the dealer’s hand without exceeding 21.
- Aces count as 1 or 11, face cards as 10, others at face value.
- Dealer draws until ≥17.
- No draws: ties count as a loss.
- Infinite deck (cards drawn with replacement).