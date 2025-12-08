* ### Player input that affects movement:

  The player movement affects where and how Cat moves.  
  |--------------------------------------------------|  
  | Boundary Input | Why It’s a Boundary                
  |----------------------|---------------------------|  
  | off-grid              | falls into infinite void  
  | blocked             | movement stopped/stuck                    
  | into restricted area    | blocked  
    
  |-----------------------------------------------------------------------------|  
  | Boundary Input | Test Data Example | Expected Outcome             
  |----------------------|------------------------------------------------------|  
  | off-grid              | Player Position: (0,0) | *Game teleports player to spawn point, if not* |\_\_\_                    |                                    | *done then character dies in a loop*  
  | blocked             | Player Position: (10,0) (stuck in obstacle)| *Game teleports player to* |\_\_\_                    |                                    | *spawn point, if not done character gets blocked*  
  | into restricted area    | Player position: (?,?) | *Game teleports player to spawn point, if* |\_\_\_\_\_                |                                            | *not done character gets blocked*

* ### Inventory limits:

  Cat’s inventor holds items such as weapons and treasures. Cat’s inventor limit is 5 items.  
  |--------------------------------------------------  
  | Boundary Input | Why It’s a Boundary                
  |----------------------|----------------------------|  
  | full inventory     | can’t collect more treasures or switch weapons   
  | empty inventory| can’t have less than 1 in inventory  
  | wrong item type| inventory rejects items  
    
  |-----------------------------------------------------------------------------|  
  | Boundary Input | Test Data Example | Expected Outcome             
  |----------------------|------------------------------------------------------|  
  | full inventory     | Player Inventory: 5/5 | *Game makes player drop item(s) before getting |\_\_                      |                                   | another, if not, player can’t collect other items*  
  | empty inventory| Player Inventory: 0/5 | *Game forces character to choose a weapon, if |\_\_                      |                                    |not, player can’t start level*             
  | wrong item type| Player Inventory: Restricted Item/5 | *Game force drops weapon, if not, |\_\_                      |                                                          | player can’t advance levels*

* ### Scoring or health calculations:

  Cat’s health indicates how many lives Cat has before restarting level.  
  |--------------------------------------------------|  
  | Boundary Input | Why It’s a Boundary                
  |----------------------|---------------------------|  
  | below 0             | stuck in loop of dying  
  | exactly 0           | player dies but no way to respawn  
  | above max       | can’t interact with enemies  
    
  |-----------------------------------------------------------------------------|  
  | Boundary Input | Test Data Example | Expected Outcome             
  |----------------------|------------------------------------------------------|  
  | below 0             | HP: \-⅓  | *Game gives restart menu, if not then character dies infinitely*   
  | exactly 0           | HP: 0/3 | *Game give restart menu, if not character doesn’t respawn*  
  | above max       | HP: 4/3  | *Game add health cap, if not character can’t interact with enemies*  
  

1. “Which logic point feels most fragile?”

   		I think the most fragile logic point is the player movement and location.

2. “What will I need to watch out for when coding this?”

		I’ll have to watch out where to set coordinates of areas restricted from players  
		

3. “Which boundary case surprised me?”

		The inventory boundary case surprised me because the boundaries were more complex than I thought
