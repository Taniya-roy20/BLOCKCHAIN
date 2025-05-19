# **PRACTICAL 6:**
# Create a contract that splits incoming Ether between 3 fixed addresses. 
**CODE: Ether Splitter Contract.sol**

     // SPDX-License-Identifier: MIT
      pragma solidity ^0.8.0;

    contract EtherSplitter {
        address payable public recipient1;
        address payable public recipient2;
        address payable public recipient3;

    constructor(address payable _addr1, address payable _addr2, address payable _addr3) {
        recipient1 = _addr1;
        recipient2 = _addr2;
        recipient3 = _addr3;
    }

    // Fallback function to receive Ether and split it
    receive() external payable {
        uint256 share = msg.value / 3;

        require(share > 0, "Amount too small to split");

        // Send each recipient their share
        recipient1.transfer(share);
        recipient2.transfer(share);
        recipient3.transfer(msg.value - 2 * share); // Remaining to 3rd to avoid rounding loss
    }
}

![image](https://github.com/user-attachments/assets/8e60fa28-6f3e-418d-a505-5108868d2f57)

# STEPS

1. Deploy the Contract

2. Send Ether to the Contract

3. Check Balances

![image](https://github.com/user-attachments/assets/258934c9-0dd6-45cb-9b62-69a54e8ac966)

![image](https://github.com/user-attachments/assets/12347f95-0818-4ef9-97d1-27b0a270af36)

