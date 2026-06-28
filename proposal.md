# PROPOSAL.md

## What I'm building
A diet-planning tool that calculates a user's maintenance calories from their personal stats and activity level, then generates a calorie and macro plan based on whether their goal is to bulk or cut.

## Who it's for / why
This is for myself. I am currently working on body recomposition and frequently need to recalculate my maintenance calories and macro targets whenever my weight, activity level, or training changes. Doing this manually each time is repetitive and time-consuming, so I want a tool that performs these calculations instantly based on updated inputs.

## The state it tracks
- Profile inputs: weight, age, gender, activity level, and weekly workout frequency outside of normal daily activity
- Goal inputs: bulk or cut, target weight, target timeframe, and whether the goal is to lean out or build muscle
- Calculated outputs: maintenance calories (TDEE), target calories, estimated time to reach the goal under different deficit/surplus rates, and the resulting macro breakdown in grams

## Core features
1. A maintenance calorie calculator using a BMR formula combined with an activity multiplier
2. A bulk/cut selector that takes a target weight and timeframe as inputs
3. A comparison of multiple deficit/surplus options (conservative, moderate, aggressive), each showing a projected timeline to reach the target weight
4. A macro breakdown that adjusts based on whether the user's goal is to lean out or build muscle
5. A reset function that allows the user to start over without refreshing the page

## What I don't know yet
- Which BMR formula to implement (Mifflin-St Jeor is the most widely used standard, so I am leaning toward that)
- How to display multiple deficit/surplus scenarios clearly without overwhelming the interface
- How to structure the macro calculation logic so the branching between "lean" and "muscle" goals stays organized rather than becoming a long chain of conditionals