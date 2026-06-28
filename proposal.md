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

## Product Requirements Document (PRD)

### 1. Product Summary
A web-based nutrition planning tool that helps users estimate their maintenance calories, explore recommended calorie targets for cutting or bulking, and receive a macro breakdown tailored to their preferred goal style. The product should be simple enough for first-time users while still offering enough flexibility for users who want multiple options and explanations.

### 2. Problem Statement
Many people who want to change their body composition need to calculate their calorie needs and macros manually. This process is repetitive, error-prone, and hard to update as their weight, activity level, or training changes. The product solves this by turning a few inputs into a clear, actionable nutrition plan within a short time.

### 3. Product Goals
Primary goals:
- Help users quickly understand how many calories they need to maintain their current weight.
- Help users choose a recommended calorie intake for a target weight and timeframe.
- Show a macro breakdown that aligns with their goal: lean, lean muscle, or bulk muscle.
- Present several plan options so users can compare tradeoffs between faster and more sustainable progress.

Non-goals for v1:
- Meal logging or food tracking
- Recipe suggestions or meal plans
- User accounts or saved plans
- Integration with wearables or fitness apps
- Medical diagnosis or personalized nutrition advice

### 4. Target Users
Primary users:
- Adults who want to lose fat, gain muscle, or improve body composition
- People who want a quick way to estimate calorie needs without doing manual math

Secondary users:
- Beginners who want simple guidance
- More experienced users who want more control and multiple scenarios

### 5. Core User Journey
1. The user enters their profile details.
2. The app calculates their maintenance calories.
3. The user enters their target weight and the time they want to reach it.
4. The app recommends a calorie deficit or surplus and shows multiple plan options.
5. The user selects a goal style: lean, lean muscle, or bulk muscle.
6. The app shows the recommended macro breakdown and explains the difference between options.
7. The user sees safety guidance for aggressive or unrealistic targets.

### 6. MVP Features
#### 6.1 Maintenance calorie calculator
The app must calculate an estimated maintenance calorie level based on the user's profile inputs.

Required inputs:
- Weight
- Age
- Gender
- Activity level
- Weekly workout sessions outside normal activity
- Unit selection for weight (kg or lb)

Expected output:
- Estimated maintenance calories
- A short explanation of the result

#### 6.2 Goal-based calorie planning
After maintenance calories are calculated, the app must let the user enter:
- Desired target weight
- Timeframe to reach that goal
- Goal type: cut or bulk

The app must then recommend:
- A calorie target for the selected goal
- A recommended deficit or surplus
- A projected timeline and comparison of several plan options

#### 6.3 Multiple plan options
The app should present several plan options rather than a single answer. At minimum, it should offer:
- Conservative
- Moderate
- Aggressive

Each option should include:
- Calorie target
- Expected weekly change rate
- Estimated time to reach the target
- A brief explanation of the tradeoff

#### 6.4 Macro breakdown
After the calorie plan is shown, the app should ask the user to choose a macro style:
- Lean
- Lean muscle
- Bulk muscle

The app should then provide a recommended macro breakdown in grams for:
- Protein
- Carbs
- Fats

The macro plan should be aligned to the selected goal style and the calorie target.

#### 6.5 Safety and guidance
The app should include gentle warnings when:
- The requested timeline is very aggressive
- The suggested calorie change seems extreme
- The target weight change rate is unrealistic

These warnings should be educational and non-judgmental.

#### 6.6 Reset function
Users should be able to start over easily without refreshing the page.

### 7. Functional Requirements
- The app must work as a single-session web app in v1.
- The app must support both kg and lb input.
- The app must calculate results instantly after the user submits their inputs.
- The app must display the results in a clear, structured way.
- The app must explain why each plan option differs.
- The app must show macros in grams and support easy comparison across plan options.
- The app must include a reset action.

### 8. UX Requirements
- The interface should be simple and guided, with a clear step-by-step flow.
- The first screen should prioritize the core inputs needed to calculate maintenance calories.
- The results view should be easy to scan and should highlight the recommended plan.
- The app should use plain language and avoid overwhelming the user with too many technical details.
- The design should feel supportive, not overly clinical.

### 9. Calculation Logic (Initial Version)
The app should use a standard calorie estimation approach based on a BMR formula and an activity multiplier. The preferred formula for v1 is Mifflin-St Jeor, but the product should be designed so the formula can be adjusted later if needed.

The app should then:
- Estimate maintenance calories
- Apply a calorie adjustment for the selected cut or bulk goal
- Generate multiple plan options with different rates of progress
- Translate the selected calorie plan into a macro breakdown based on the chosen style

### 10. Macro Strategy Guidance
The macro breakdown should be designed around the goal style:
- Lean: higher protein, moderate fats, lower carbs
- Lean muscle: high protein, moderate carbs, moderate fats
- Bulk muscle: high protein, higher carbs, moderate fats

Protein should remain a priority in all cases, and the remaining calories should be distributed between carbs and fats based on the selected goal style.

### 11. Success Metrics
Success will be measured by whether the product helps the user accomplish the core outcome:
- The user can enter their information and receive a clear plan quickly
- The user understands their maintenance calories and the calorie target for their goal
- The user leaves with a practical macro target for the selected goal style

### 12. Risks and Considerations
- Nutrition needs vary widely by individual, so the app should present results as estimates.
- Aggressive goals may be unrealistic, so the app should include warnings.
- The app should avoid presenting the results as medical advice.

### 13. MVP Scope
The first version should focus only on the core value:
- Maintenance calorie calculation
- Recommended deficit or surplus based on target weight and time
- Recommended macro breakdown for the selected goal style
- Multiple plan options with tradeoffs
- Reset and simple web-based interaction