# Agent Based Covid Model
Created by Jayce Slesar, Brandon Lee, Carter Ward under the guidance of Jason Bates, John Hanley, Vitor Mori at the University of Vermont.
Last Updated October 12th, 2021

A heavily paramaterizeable physics simulation to show how aersols spread within enviroments like offices and classrooms

One individual is 'infected' and releases infected aerosols into the room. Using diffusion the model determines where the 'infected' aerosols \
move to.

Example of 3 different simulations:

![Exaple](assets/blanket.png)

## Parameters: (found in sim_params.json) with units
### IMPORTANT: The self.time_length variable in room.py controls the time step. Keeping it at 1 means that each step is 1 second.
- seed: the number to choose the seed for random variables in a simulation
- rows_people: the number of rows for the simulation (should be odd)
- cols_people: the number of cols for the simulation (should be odd)
- have_teacher: boolean value for if there is a teacher in the room (is at the front)
- moving_agent: boolean value to introduce a moving agent into the simulation
- iterations: the number of steps to take (each iteration/setp is a second if step_size is set to one)
- fan_cycles: a paramater to control the fan animation
- window_height: size paramater for the simulation visualization
- window_width: size paramater for the simulation visualization
- source_row: the row that the source is in
- source_col: the column that the source is in (produces air into the system -- the fan)
- source_ach: the air changes per hour of the source
- sink_row: the row that the sink is in
- snk_col: the column that the sink is in (takes in and evacuates air at a rate)
- sink_ach: the air changes per hour of the sink
- mic: boolean valuue if the teacher has a microphone or not (cuts production rate in half if true)
- inhale_mask_factor: the starting rate/fraction of inhaling given an agent has a mask
- exhale_mask_factor: rate/fraction of exhalation given a mask (N95 masks reduce outtake by 95% and so on...)
- breathe_volume: volume breathed in --> (concentration*.0005 cubic meters)*.233 seconds
- aerosol_mass: mass in mols per aerosol (kg)
- agent_volume: volume the agent takes up in the respective cell (cubic meters)
- cell_width: width of the cell (m)
- cell_height: height of the cell (m)
- diffusivity: rate of diffusion (meters squared/second)
- micro_current_factor: how much micro currents affect diffusivity
- color_upper_limit: cap for the color of a cell (colored by how much infected aerosol is inside)

Production rates from https://www.medrxiv.org/content/10.1101/2021.02.07.21251309v2.full.pdf

# Installation:

`$ git clone https://github.com/jayceslesar/covid-agents.git` \
`$ cd covid-agents` \
Use of virtual environment is recommended \
`$ pip install -r requirements.txt`

# How to Run:

Running `main.py` with a configuration of `sim_params.json` will run the model.
Upon running, it will ask if you would like to save the data into a directory. Screenshots can be saved to create a .gif of the model run. \
A visual will appear to show what is happening currently during the simulation. Darker blue means more 'infected' aerosol.

# General Usage:

Easy paramaters to change include source and sink locations, the size of the grid, who is infected, and how effective masks are. \
The data output into the `data` folder is a csv where each row is a different cell with an agent at a timestep. Blank spaces are excluded so it is easier to analyze how much total infected aerosol a given agent as inhaled.

# References:
Production Rates: \
https://www.medrxiv.org/content/10.1101/2021.02.07.21251309v2.full.pdf \
https://www.pnas.org/content/118/8/e2021830118 \

Breath Capacity: \
https://www.bbc.co.uk/bitesize/guides/z3xq6fr/revision/2#:~:text=Tidal%20volume%20(TV)%20is%20the,is%206%20litres%20per%20minute \

Breaths per Minute: \
https://www.hopkinsmedicine.org/health/conditions-and-diseases/vital-signs-body-temperature-pulse-rate-respiration-rate-blood-pressure#:~:text=Normal%20respiration%20rates%20for%20an,to%2016%20breaths%20per%20minute \

Inactivation Rate of COVID-19: \
https://www.reuters.com/article/us-health-coronavirus-study/coronavirus-can-persist-in-air-for-hours-and-on-surfaces-for-days-study-idUSKBN2143QP \

Aerosol Info: \
https://www.cdc.gov/niosh/topics/aerosols/pdfs/Aerosol_101.pdf \
http://web.mit.edu/fluids-modules/www/low_speed_flows/2-7Aerosol.pdf \

Production Rates: \
https://jamanetwork.com/journals/jamanetworkopen/fullarticle/2768712 \
https://academic.oup.com/cid/advance-article/doi/10.1093/cid/ciaa1283/5898624 \


