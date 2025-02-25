# BTC Trading Project
Welcome to the BTC Trading Project! This repository contains a sophisticated trading bot designed to trade Bitcoin using advanced reinforcement learning techniques. Whether you're an experienced trader or a developer interested in financial algorithms, our project has something to offer.

## Overview
The BTC Trading Project leverages the power of reinforcement learning to create a trading agent that can make informed decisions in the highly volatile Bitcoin market. The project uses the Proximal Policy Optimization (PPO) algorithm from the Stable Baselines library, integrated with a custom trading environment.

## Features
* Custom Trading Environment: Tailored specifically for Bitcoin trading, providing realistic market simulations.
* Advanced RL Algorithm: Utilizes PPO, a state-of-the-art reinforcement learning algorithm known for its efficiency and performance.
* Easy to Train: The agent can be trained with minimal setup, making it accessible for both beginners and professionals.
* Model Saving: Save and reload trained models for continuous learning and improvement.

## Getting Started
### Prerequisites
* Python 3.7+
* Gym
* Stable Baselines3

### Installation
1. Clone the repository:

   ```bash
   git clone https://github.com/samwinston1996/BTC_Trading_Project.git
   cd BTC_Trading_Project

2. Install the required packages:

   ```bash
   pip install -r requirements.txt

## Usage
1. Initialize the custom trading environment and train the agent:

    ```code
    import gym
    from stable_baselines3 import PPO
    from env.trading_env import TradingEnv
    
    # Initialize the custom environment
    env = TradingEnv()
    
    # Initialize RL agent using PPO
    model = PPO('MlpPolicy', env, verbose=1)
    
    # Train the agent
    model.learn(total_timesteps=50000)
    
    # Save the trained model
    model.save('models/agent_model')
    
    # Close the environment
    env.close()
    
    print("Training complete and model saved.")


2. To evaluate the trained model, simply load it and run it in the environment:

  ```code
  model = PPO.load('models/agent_model')
  obs = env.reset()
  while True:
      action, _states = model.predict(obs)
      obs, rewards, done, info = env.step(action)
      if done:
          obs = env.reset()
