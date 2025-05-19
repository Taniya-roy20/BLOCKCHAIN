# **Practical 4: Top donor**
# **Write a contract where people can donate Ether and the top 3 donors are tracked.**
**code: TopDonors.sol**

     // SPDX-License-Identifier: MIT
      pragma solidity ^0.8.0;

     contract TopDonors {
         // Store donation amount per address
          mapping(address => uint) public donations;

    // Struct to hold donor info
    struct Donor {
        address addr;
        uint amount;
    }

    // Fixed-size array for top 3 donors
    Donor[3] public topDonors;

    // Public donation function
    function donate() public payable {
        require(msg.value > 0, "Donation must be greater than 0");

        // Add to sender's total donation
        donations[msg.sender] += msg.value;

        // Update top donors
        _updateTopDonors(msg.sender);
    }

    // Internal function to update top 3
    function _updateTopDonors(address donor) internal {
        uint currentAmount = donations[donor];

        // Check if donor already in top list
        for (uint i = 0; i < 3; i++) {
            if (topDonors[i].addr == donor) {
                topDonors[i].amount = currentAmount;
                _sortTopDonors();
                return;
            }
        }

        // Check if this donor beats any existing top donor
        for (uint i = 0; i < 3; i++) {
            if (currentAmount > topDonors[i].amount) {
                // Replace and sort
                topDonors[i] = Donor(donor, currentAmount);
                _sortTopDonors();
                return;
            }
        }
    }

    // Bubble sort the topDonors array in descending order
    function _sortTopDonors() internal {
        for (uint i = 0; i < topDonors.length; i++) {
            for (uint j = i + 1; j < topDonors.length; j++) {
                if (topDonors[j].amount > topDonors[i].amount) {
                    Donor memory temp = topDonors[i];
                    topDonors[i] = topDonors[j];
                    topDonors[j] = temp;
                }
            }
        }
    }

    // Get top donor by index: 0 (top), 1, or 2
    function getTopDonor(uint index) public view returns (address, uint) {
        require(index < 3, "Index out of bounds");
        Donor memory d = topDonors[index];
        return (d.addr, d.amount);
     }
   }

   ![image](https://github.com/user-attachments/assets/351ed70b-3c9f-43c7-8ef0-f8e30c416c1d)
   ![image](https://github.com/user-attachments/assets/c9a981d1-2842-4018-beea-3ea75458c0ac)
   ![image](https://github.com/user-attachments/assets/271b8f1f-d2f0-4fc9-af90-c061a2c12873)

# STEPS
   
Test in Remix
    
Deploy the contract in Remix using Remix VM (Prague).

Use the Value field (in ETH) to simulate donations:

Set Value to 1 Ether, 0.5, 2, etc.

Click donate() using different accounts.

Use getTopDonor(0), getTopDonor(1), and getTopDonor(2) to view top donors.

![image](https://github.com/user-attachments/assets/b1916703-715b-4f75-aeca-658d1d136136)
![image](https://github.com/user-attachments/assets/06f773f8-b8a6-475f-a5d3-e61366727904)
![image](https://github.com/user-attachments/assets/55f5ad60-f79b-4337-b02d-5cbdeca70835)







   


