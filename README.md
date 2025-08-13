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

If you are curious to understand in-depth, <span class="clickable" onclick="toggleDetails()">click here</span>

<div id="details" class="details-hidden">
  <h3>Technical Deep Dive</h3>
  
  <h4>Neural Network Architecture</h4>
  <p>The AI uses a feed-forward neural network with:</p>
  <ul>
    <li><strong>3 Inputs:</strong> Bird's Y position, distance to top pipe, distance to bottom pipe</li>
    <li><strong>1 Output:</strong> Decision to jump (0-1 threshold)</li>
    <li><strong>Activation:</strong> Tanh function for smooth decision making</li>
  </ul>

  <h4>NEAT Algorithm Process</h4>
  <ol>
    <li><strong>Initialization:</strong> Creates 50 random neural networks</li>
    <li><strong>Evaluation:</strong> Each network plays the game and gets a fitness score</li>
    <li><strong>Selection:</strong> Best performing networks are selected for reproduction</li>
    <li><strong>Mutation:</strong> Networks are mutated (weights, connections, topology)</li>
    <li><strong>Crossover:</strong> Successful networks combine their "genes"</li>
    <li><strong>New Generation:</strong> Process repeats with evolved population</li>
  </ol>

  <h4>Fitness Function</h4>
  <ul>
    <li>+0.1 fitness per frame survived</li>
    <li>+5 fitness per pipe passed</li>
    <li>-1 fitness for collisions</li>
    <li>Goal: Maximize survival time and pipe navigation</li>
  </ul>

  <h4>Training Process</h4>
  <p>The system runs for up to 50 generations, with each generation typically showing improved performance. Early generations may have birds that flap randomly or die quickly, while later generations develop sophisticated strategies for navigating through pipes.</p>

  <h4>Key Components</h4>
  <ul>
    <li><strong>Bird Physics:</strong> Gravity simulation with terminal velocity</li>
    <li><strong>Pipe Generation:</strong> Random heights with consistent gaps</li>
    <li><strong>Collision Detection:</strong> Pixel-perfect collision using Pygame masks</li>
    <li><strong>Real-time Visualization:</strong> Watch evolution happen live</li>
  </ul>
</div>

## Contributing

Contributions are welcome! Feel free to submit a pull request or open an issue if you find any bugs or have suggestions for improvements.

<style>
.clickable {
  color: #0066cc;
  text-decoration: underline;
  cursor: pointer;
  font-weight: bold;
}

.clickable:hover {
  color: #003366;
}

.details-hidden {
  display: none;
  background-color: #f8f9fa;
  border: 1px solid #dee2e6;
  border-radius: 8px;
  padding: 20px;
  margin: 20px 0;
  box-shadow: 0 2px 4px rgba(0,0,0,0.1);
}

.details-visible {
  display: block;
  animation: fadeIn 0.3s ease-in;
}

@keyframes fadeIn {
  from { opacity: 0; transform: translateY(-10px); }
  to { opacity: 1; transform: translateY(0); }
}

#details h3 {
  color: #2c3e50;
  border-bottom: 2px solid #3498db;
  padding-bottom: 10px;
  margin-bottom: 20px;
}

#details h4 {
  color: #34495e;
  margin-top: 25px;
  margin-bottom: 10px;
}

#details ul, #details ol {
  margin-left: 20px;
  margin-bottom: 15px;
}

#details li {
  margin-bottom: 8px;
  line-height: 1.5;
}

#details p {
  line-height: 1.6;
  margin-bottom: 15px;
}
</style>

<script>
function toggleDetails() {
  const details = document.getElementById('details');
  if (details.classList.contains('details-hidden')) {
    details.classList.remove('details-hidden');
    details.classList.add('details-visible');
  } else {
    details.classList.remove('details-visible');
    details.classList.add('details-hidden');
  }
}
</script>
