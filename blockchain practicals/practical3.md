
## Develop a contract that only allows the deployer (owner) to call a specific function (use modifiers).
```
// SPDX-License-Identifier: MIT
pragma solidity ^0.8.0;

contract OwnerOnly {
    address public owner;

    constructor() {
        owner = msg.sender;
    }

    modifier onlyOwner() {
        require(msg.sender == owner, "Not the owner");
        _;
    }

    string public secret;

    function setSecret(string memory _secret) public onlyOwner {
        secret = _secret;
    }
}

```
![image](https://github.com/user-attachments/assets/c72ed9a9-1e10-433f-ae73-2ef657a3a936)

![image](https://github.com/user-attachments/assets/94bf1ca3-7591-4661-bb28-79ef7c2b1061)

![image](https://github.com/user-attachments/assets/615c99f8-6e87-4329-93f9-9263a0b077a8)

