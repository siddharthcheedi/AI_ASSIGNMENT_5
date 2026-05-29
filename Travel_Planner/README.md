# AI-Based Travel Planner

## Overview

This project is an AI-Based Travel Planner that creates personalized travel itineraries based on a user's destination, budget, interests, and food preferences.

The system uses different knowledge bases such as tourist attractions, food recommendations, beverage pairings, and cost estimation to generate a complete travel plan.

The goal is to help users plan trips more efficiently while staying within their budget and preferences.

---

# Project Structure

## places_db.py

This file contains information about tourist attractions.

For each attraction, it stores:

- Attraction name
- Category
- Entry fee
- Visit duration
- Best time to visit
- Rating

The planner uses this information to recommend places that match the user's interests.

---

## food.py

This module recommends food based on:

- Destination
- Dietary preferences
- User selections

Examples include:

- Vegetarian meals
- Vegan meals
- Local specialties

The recommendations are filtered according to the user's dietary requirements.

---

## wine.py

This module contains beverage pairing knowledge.

It suggests suitable beverages for recommended food items.

Examples:

- Pasta → Red Wine
- Sushi → Sake
- Vegetarian Meals → Green Tea or Mocktails

The information is stored as simple relationships between foods and beverages.

---

## planner.py

This is the main planning engine.

It creates travel itineraries based on:

- User interests
- Attraction ratings
- Available travel days
- Destination

Activities are organized into a day-by-day schedule.

Example:

Morning:
- Visit historical attraction

Afternoon:
- Explore local market

Evening:
- Try local cuisine

---

## cost.py

This module estimates the total cost of the trip.

It considers:

- Attraction fees
- Food expenses
- Accommodation costs
- Transportation costs

If the estimated cost exceeds the budget, the planner attempts to replace expensive activities with lower-cost alternatives.

---

## travel.py

This is the main file of the project.

It combines all other modules and performs the following tasks:

- Accepts user input
- Generates recommendations
- Creates the itinerary
- Estimates trip cost
- Displays the final travel plan

---

# Features

- Personalized travel planning
- Tourist attraction recommendations
- Food recommendations
- Beverage pairing suggestions
- Budget estimation
- Cost optimization
- Multi-day itinerary generation
- Interest-based attraction selection

---

# How the System Works

1. The user enters travel details such as destination, duration, budget, interests, and dietary preferences.

2. The planner retrieves suitable attractions from the places database.

3. Food recommendations are generated based on the destination and dietary restrictions.

4. Beverage pairings are suggested using the beverage knowledge base.

5. A day-by-day travel itinerary is generated.

6. The total trip cost is estimated.

7. If the estimated cost exceeds the budget, lower-cost alternatives are selected where possible.

8. The final travel plan is displayed to the user.

---

# Sample Input

Destination: Kyoto

Duration: 3 Days

Budget: 600

Diet: Vegetarian

Interests: Culture, Food

---

# Sample Output

Day 1

Morning:
- Fushimi Inari Shrine

Afternoon:
- Nishiki Market

Evening:
- Vegetarian Japanese Dinner

Estimated Cost: $180

Recommended Beverage:
- Green Tea

---

# Running the Project

Run the program:

```bash
python travel.py
```

Or provide inputs directly:

```bash
python travel.py Kyoto 3 moderate 600 vegetarian yes Culture,Food
```

---

# Conclusion

This project demonstrates how AI can be used to create personalized travel plans by combining multiple knowledge bases such as tourist attractions, food recommendations, beverage pairings, and cost estimation.

The system generates practical travel itineraries that match user preferences while helping users stay within their budget.
