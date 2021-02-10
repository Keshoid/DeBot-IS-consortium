# Msg Interface

**Status**: Proposed

| Name      | ID                                                                |
| :-------- | :---------------------------------------------------------------- |
| Msg       | 96517b3e086fdd7dbd0fb916ab59aad1c86bcc6e18376bfa847ac91fefb083a6  |

## Description

Allows to send external messages to destination smart contracts.

## Functions

`send` - sends external inbound message to destination smart contract.

arguments: 

    answerId: uint32 - function id of result callback

	message: cell - unsigned message encoded into tree of cells
    
    defSigner: bool - true if message must be signed by default signer.

returns: 

	status: SendStatus - structure for storing result of message handling by destination smart contract. Structure has the folowing fields:
		
		succeeded - true if transaction generated by msg completed successfully.

		code - exit code of destination smart contract.

## Declaration in Solidity

```jsx

struct SendStatus {
	bool succeeded; 
	int32 code;
}

interface IMsg {

    function send(uint32 answerId, TvmCell message, bool defSigner) external returns (SendStatus status);

}
```

## Declaration in C++

```cpp
namespace tvm { namespace schema {

struct SendStatus {
	bool succeeded; 
	int32 code;
}

__interface IMsg {

	[[internal, answer_id]]
	SendStatus send(cell message, bool def_signer);
	
};

}}
```

## Code Example

### Solidity

Example.sol

### C++

TODO: add later.