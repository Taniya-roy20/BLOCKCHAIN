# **Practical 3: OwnerRestricted**
# **Develop a contract that only allows the deployer (owner) to call a specific function (use modifiers).**
**Code: OwnerRestricted.sol**

      // SPDX-License-Identifier: MIT
        pragma solidity ^0.8.0;
  
        contract OwnerRestricted {
            address public owner;

    // Set the deployer as the owner when the contract is deployed
    constructor() {
        owner = msg.sender;
    }

    // Modifier that allows only the owner to execute a function
    modifier onlyOwner() {
        require(msg.sender == owner, "Not the contract owner");
        _;
    }

    // Example function that only the owner can call
    function secretFunction() public onlyOwner returns (string memory) {
        return "This is a secret only for the owner!";
    }

    // Anyone can call this function
    function publicFunction() public pure returns (string memory) {
        return "This is a public function";
     }
    }

![image](https://github.com/user-attachments/assets/cc7c5e3a-5bc1-43f6-a80a-4bfd68261077)

# STEPS
**How to Test in Remix**

Paste the code into a new file OwnerRestricted.sol.

Compile the contract.

Deploy using an account (this account becomes the owner).

Call secretFunction() – it should succeed.

Change the account (top-left in Remix) and call secretFunction() again – it should fail with: Not the contract owner.

![image](https://github.com/user-attachments/assets/5f9ff87d-d39d-43a4-9b31-c04f8bdb4e6a)
![image](https://github.com/user-attachments/assets/91a1cd95-3863-42fc-bdd8-4772e5005408)



# OUTPUT
![image](https://github.com/user-attachments/assets/4c0e2a91-55aa-4766-9562-74bde8f41efe)
