## Create a voting system with multiple candidates. Each address can vote only once.

```
// SPDX-License-Identifier: MIT
pragma solidity ^0.8.0;

contract VotingSystem {
    mapping(address => bool) public hasVoted;
    mapping(string => uint) public votes;
    string[] public candidates;

    constructor(string[] memory _candidates) {
        candidates = _candidates;
    }

    function vote(string memory _candidate) public {
        require(!hasVoted[msg.sender], "Already voted!");
        bool valid = false;
        for (uint i = 0; i < candidates.length; i++) {
            if (keccak256(bytes(candidates[i])) == keccak256(bytes(_candidate))) {
                valid = true;
                break;
            }
        }
        require(valid, "Invalid candidate");
        votes[_candidate]++;
        hasVoted[msg.sender] = true;
    }
}

```
![image](https://github.com/user-attachments/assets/37962cfc-cfdf-43ab-a52a-f8a0831b5c93)

![image](https://github.com/user-attachments/assets/2ace6d59-8b88-404d-9c8e-816d95ab65e8)

![image](https://github.com/user-attachments/assets/7e67392a-0c88-4c44-ac67-80e6b7cd461a)

