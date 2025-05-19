# **Practical 5: Auction Contract**
# **Implement a simple auction system where users can place bids, and the highest bidder wins.**

**code: AuctionContract.sol**


    // SPDX-License-Identifier: MIT
       pragma solidity ^0.8.0;

      contract SimpleAuction {
          address public owner;
          address public highestBidder;
          uint public highestBid;
          bool public auctionEnded;

    mapping(address => uint) public pendingReturns;

    constructor() {
        owner = msg.sender;
    }

    // Place a bid
    function bid() public payable {
        require(!auctionEnded, "Auction already ended");
        require(msg.value > highestBid, "There already is a higher or equal bid");

        if (highestBid != 0) {
            // Refund the previously highest bidder
            pendingReturns[highestBidder] += highestBid;
        }

        highestBidder = msg.sender;
        highestBid = msg.value;
    }

    // Withdraw a bid that was overbid
    function withdraw() public returns (bool) {
        uint amount = pendingReturns[msg.sender];
        require(amount > 0, "No amount to withdraw");
        pendingReturns[msg.sender] = 0;

        (bool success, ) = payable(msg.sender).call{value: amount}("");
        if (!success) {
            pendingReturns[msg.sender] = amount;
            return false;
        }
        return true;
    }

    // End the auction and send funds to the owner
    function endAuction() public {
        require(msg.sender == owner, "Only owner can end the auction");
        require(!auctionEnded, "Auction already ended");

        auctionEnded = true;

        // Send the highest bid to the owner
        payable(owner).transfer(highestBid);
    }
   }

   ![image](https://github.com/user-attachments/assets/91c0c4c3-4324-4062-a313-fb60df293e61)
   ![image](https://github.com/user-attachments/assets/9021e3d7-5a98-475d-b892-69c0db79cda3)

# STEPS

**How to Test in Remix**

Deploy contract

Use different accounts in Remix (top-left dropdown) to:

Place bids using bid() with different ETH values

Call highestBid() and highestBidder() to check the current leader

Call endAuction() with the owner account

Use withdraw() if a non-winner wants to get refunded

![image](https://github.com/user-attachments/assets/bbc94d6b-9e6e-4508-9361-5e09751caada)
![image](https://github.com/user-attachments/assets/acafed5b-9d4c-455d-a7dd-ff7e6b5756ea)





