Implementation of HOOD

# Installation creating conda environment 
conda create -n obj python=3.8
conda activate obj
# Installing Robosuite with pushing domain (from source)
git clone https://github.com/kvablack/robosuite.git
conda activate obj
cd robosuite
copy mujoco download to: ~/.mujoco/mujoco200
copy mujoco key to ~/.mujoco/mjkey.txt
pip install -r requirements.txt
https://robosuite.ai/docs/installation.html
# install remaining components
conda install pytorch torchvision torchaudio cudatoolkit=10.2 -c pytorch
conda install imageio
pip install opencv-python
conda install psutil
pip install pyyaml

generate Random conditionals
python generate_random.py --env RandomDistribution --record-rollouts ./data/RandomDistribution/random/ --num-frames 1000
python generate_random.py --env RandomDistribution --record-rollouts ./data/RandomDistribution/random_conditional/ --num-frames 1000 --variant conditional
python generate_random.py --env RandomDistribution --record-rollouts ./data/RandomDistribution/random_conditional_passive/ --num-frames 1000 --variant conditional_passive
python generate_random.py --env RandomDistribution --record-rollouts ./data/RandomDistribution/random_passive_only/ --num-frames 1000 --variant passive_only
python generate_random.py --env RandomDistribution --record-rollouts ./data/RandomDistribution/random_passive_only_noise/ --num-frames 1000 --variant passive_only_noise


generate Breakout generation:
python generate_random.py --env Breakout --record-rollouts ./data/breakout/random/

generate Full Breakout generation:
python generate_random.py --env Breakout --record-rollouts ./data/full/breakout/small/random/ --num-frames 50000

generate Robopushing generation:
python generate_random.py --env RoboPushing --record-rollouts ./data/robopushing/testrun/random --num-frames 5000
python generate_random.py --env RoboPushing --record-rollouts ./data/robopushing/fixed/testrun/random/ --num-frames 5000 --fixed-limits
python generate_random.py --env RoboPushing --record-rollouts ../data/robopushing/random/ --num-frames 5000


generate Asteroids generation:
python generate_random.py --env Asteroids --record-rollouts ./data/asteroids/random/ --num-frames 10000 --fixed-limits

python generate_random.py --env Asteroids --record-rollouts ./data/asteroids/coordinate_turn/random/ --variant coordinate_turn --num-frames 10000 --fixed-limits


generate Sokoban generation:
python generate_random.py --env Sokoban --record-rollouts ./data/sokoban/random/ --num-frames 10000

python generate_random.py --env Sokoban --record-rollouts ./data/sokoban/fixed/few_obs/random/ --variant few_obs --num-frames 10000 --fixed-limits

python generate_random.py --env Asteroids --demonstrate --num-frames 5000

generate Taxicar Training:
python generate_random.py --env TaxiCar --record-rollouts ./data/TaxiCar/random/ --num-frames 10000

generate airhockey generation:
python generate_random.py --env AirHockey --record-rollouts ./data/airhockey/ --demonstrate --num-frames 5000

