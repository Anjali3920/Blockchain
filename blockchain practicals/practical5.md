## Implement a simple auction system where users can place bids, and the highest bidder wins.
```
// SPDX-License-Identifier: MIT
pragma solidity ^0.8.0;

contract SimpleAuction {
    address public highestBidder;
    uint public highestBid;

    function bid() public payable {
        require(msg.value > highestBid, "Bid too low");

        if (highestBid != 0) {
            payable(highestBidder).transfer(highestBid);
        }

        highestBidder = msg.sender;
        highestBid = msg.value;
    }
}

```

![image](https://github.com/user-attachments/assets/bc9f4cf8-bf64-4e8d-86c4-cf656e27f978)


![image](https://github.com/user-attachments/assets/e579355d-41b1-4e84-8431-d8e259485fca)
