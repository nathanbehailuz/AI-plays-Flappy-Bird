# AI Plays Flappy Bird

This project demonstrates how an AI agent can be trained to play the popular game Flappy Bird using reinforcement learning. The AI uses the NEAT (NeuroEvolution of Augmenting Topologies) algorithm to evolve neural networks that control the bird.

## Features

- **NEAT Algorithm:** Utilizes NEAT for evolving neural networks.
- **Game Simulation:** Simulates the Flappy Bird game for the AI to train and play.
- **Visualization:** Real-time visualization of the AI playing the game.

## Installation

1. Clone the repository:
   ```bash
   git clone https://github.com/nathanbehailuz/AI-plays-Flappy-Bird.git
   cd AI-plays-Flappy-Bird
   ```
2. Install the required dependencies:
   ```bash
   pip install -r requirements.txt
   ```

## Usage

To train the AI and watch it play, simply run:

```bash
python flappy_bird.py
```

## How It Works

<details>
<summary><strong>Click here to understand in-depth how the AI works</strong></summary>

### Technical Deep Dive

#### Neural Network Architecture

The AI uses a feed-forward neural network with:

- **3 Inputs:** Bird's Y position, distance to top pipe, distance to bottom pipe
- **1 Output:** Decision to jump (0-1 threshold)
- **Activation:** Tanh function for smooth decision making

#### NEAT Algorithm Process

1. **Initialization:** Creates 50 random neural networks
2. **Evaluation:** Each network plays the game and gets a fitness score
3. **Selection:** Best performing networks are selected for reproduction
4. **Mutation:** Networks are mutated (weights, connections, topology)
5. **Crossover:** Successful networks combine their "genes"
6. **New Generation:** Process repeats with evolved population

#### Fitness Function

- +0.1 fitness per frame survived
- +5 fitness per pipe passed
- -1 fitness for collisions
- Goal: Maximize survival time and pipe navigation

#### Training Process

The system runs for up to 50 generations, with each generation typically showing improved performance. Early generations may have birds that flap randomly or die quickly, while later generations develop sophisticated strategies for navigating through pipes.

#### Key Components

- **Bird Physics:** Gravity simulation with terminal velocity
- **Pipe Generation:** Random heights with consistent gaps
- **Collision Detection:** Pixel-perfect collision using Pygame masks
- **Real-time Visualization:** Watch evolution happen live

</details>

## Contributing

Contributions are welcome! Feel free to submit a pull request or open an issue if you find any bugs or have suggestions for improvements.
