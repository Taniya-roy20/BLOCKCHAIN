# **PRACTICAL 1**
# **Create a voting system with multiple candidates. Each address can vote only once.**
**Objective :**

Create and deploy a simple voting system in Solidity where:

Each voter can vote only once.

Each candidate has a vote count.

Users can view candidate details and vote count.

votingSystem.sol

        // SPDX-License-Identifier: MIT
        pragma solidity ^0.8.0;

       contract Voting {
             struct Candidate {
                  string name;
                  uint voteCount;
    }

    address public owner;
    mapping(address => bool) public hasVoted;
    Candidate[] public candidates;

    constructor(string[] memory candidateNames) {
        owner = msg.sender;
        for (uint i = 0; i < candidateNames.length; i++) {
            candidates.push(Candidate(candidateNames[i], 0));
        }
      }

    function vote(uint candidateIndex) public {
        require(!hasVoted[msg.sender], "You have already voted.");
        require(candidateIndex < candidates.length, "Invalid candidate.");
        hasVoted[msg.sender] = true;
        candidates[candidateIndex].voteCount++;
    }
}



     

![image](https://github.com/user-attachments/assets/d4039479-7f32-4f62-a971-48f29a350e31)
![image](https://github.com/user-attachments/assets/f38cbcd2-2146-4830-8116-29f9039b2b91)

# **Deployment & Testing Steps (in Remix)**

# Step 1: Setup Environment

Open Remix IDE

Create a new file votingSystem.sol and paste the code above.

Compile with Solidity compiler version 0.8.0 (or compatible).

Go to the Deploy & Run Transactions tab.

Set Environment to Remix VM (Prague).

![image](https://github.com/user-attachments/assets/d6fae800-cd4f-4dbd-b4dc-6f2ea8b2bde4)

# Step 2: Deploy Contract

In the Deploy section, enter candidate names as a string array:

    ["Alice", "Bob", "Charlie"]
    
Click Deploy.

![image](https://github.com/user-attachments/assets/aca619dc-3ba7-4036-a0cb-b068fb562c0f)

# Step 3: Interact With Contract

Check candidates:

Expand candidates public array.

Use indexes 0, 1, and 2 to view:

          name

          voteCount

 **Vote:**

In the vote function, enter a candidate index (e.g., 2 for Charlie).

Click transact.
![image](https://github.com/user-attachments/assets/6f186cae-f69c-4372-b3ba-7ffd490fa5b5)

# OUTPUT 
![image](https://github.com/user-attachments/assets/eff48137-1349-4bb1-81a4-304277828509)
![image](https://github.com/user-attachments/assets/1bba8d2a-b086-4458-9cf5-38a09141570d)
![image](https://github.com/user-attachments/assets/ed44de0f-0f43-40c4-9d58-77cc38855757)
![image](https://github.com/user-attachments/assets/f1965c1b-ed42-4995-8673-f009365af7ff)
![image](https://github.com/user-attachments/assets/40315d4f-f7b3-436d-b2b8-0cdde291c829)
![image](https://github.com/user-attachments/assets/1e017933-49f6-431f-8655-a263cd7f4ca3)
![image](https://github.com/user-attachments/assets/b38f7616-e2c5-49d0-a25b-e9a743fec11b)
![image](https://github.com/user-attachments/assets/76b1f73d-0f76-4423-a73b-5a84e7e57627)
![image](https://github.com/user-attachments/assets/9f4e0367-68ba-4650-bf30-d6656e0516b8)
