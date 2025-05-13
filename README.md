# Snatch Movement Analysis
Snatch Analysis Toolkit: From Data to Insights
What This Project Does
I've built a system that breaks down weightlifting technique by analyzing snatch movements. After processing dozens of lifts, it helps visualize:

How your body moves during the lift

Where you generate the most force

The exact path the barbell takes

How your hip angles change throughout

Under the Hood
Cleaning Up the Data (MATLAB)
The magic starts in Snatch_Analysis.m where we:

Grab the Data: Pull in all those CSV files from training sessions

Smooth Things Out:

matlab
[b,a] = butter(4, 5/(fs/2), 'low');
filtered_data = filtfilt(b, a, raw_data);
This filter keeps the important movement patterns while ditching the jittery noise

Line Up the Timing: Stretches or squeezes each lift to match the same timeline

Crunch the Numbers: Calculates forces, angles, and key moments in the lift

What You Actually See
The Snatch_Statistics.m script creates:

Charts That Tell a Story:

How your force changes through each phase

When your hips open during the pull

An Animation That Brings It to Life:

matlab
ani = FuncAnimation(fig, @update, frames=100, interval=50);
Watch your average lift unfold with:

The barbell's path

Your body positioning

All moving together just like in real life

Where Everything Lives
/snatch-analysis
├── /data
│   ├── /raw              # The original lift recordings
│   └── /processed        # Cleaned-up numbers ready for analysis
├── /scripts
│   ├── preprocessing/    # The data cleaning crew
│   └── analysis/         # Where the insights get made
├── /results
│   ├── /figures          # Those "aha!" moment charts
│   └── /animations       # Your lift in motion
└── /infos                # All the how-to docs

Looking Ahead: Building a Smart Weightlifting Coach
As I continue developing this system, here's where I'm taking it next:

Collecting Better Movement Data
Right now I'm using Kinovea to record lifts from the side view (about 2-3 meters away at a 90° angle). This gives me clean footage to analyze the key positions. I'm building up to 100+ snatch videos to train a proper movement recognition system.

Teaching the Computer to "See" Proper Form
With enough quality recordings, I'll implement an LSTM neural network that can:

Automatically identify different phases of the lift

Spot when my form starts breaking down

Predict whether a lift will succeed based on early movement patterns

How This Helps Lifters
Eventually this could become:

A real-time coaching assistant that gives form feedback

A diagnostic tool to identify weak points in the lift

A way to track progress beyond just weight lifted
