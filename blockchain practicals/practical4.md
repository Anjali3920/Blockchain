
## Write a contract where people can donate Ether and the top 3 donors are tracked.
```
// SPDX-License-Identifier: MIT
pragma solidity ^0.8.0;

contract Donations {
    struct Donor {
        address donor;
        uint amount;
    }

    Donor[] public topDonors;

    function donate() public payable {
        require(msg.value > 0, "Send some ether");

        Donor memory newDonor = Donor(msg.sender, msg.value);
        topDonors.push(newDonor);
        
        // Sort topDonors
        for (uint i = 0; i < topDonors.length; i++) {
            for (uint j = i + 1; j < topDonors.length; j++) {
                if (topDonors[j].amount > topDonors[i].amount) {
                    Donor memory temp = topDonors[i];
                    topDonors[i] = topDonors[j];
                    topDonors[j] = temp;
                }
            }
        }

        if (topDonors.length > 3) {
            topDonors.pop(); // Keep only top 3
        }
    }

    function getTopDonors() public view returns (Donor[] memory) {
        return topDonors;
    }
}

```
![image](https://github.com/user-attachments/assets/f5ec615e-9693-49a9-ad6f-0ef400788c25)
![image](https://github.com/user-attachments/assets/80a7881e-ce38-4d03-8803-1290f64834d3)
