
# RadicalxChange contest details

- Join [Sherlock Discord](https://discord.gg/MABEWyASkp)
- Submit findings using the issue page in your private contest repo (label issues as med or high)
- [Read for more details](https://docs.sherlock.xyz/audits/watsons)

# Q&A

### Q: On what chains are the smart contracts going to be deployed?
Optimism, EVM-Compatible Chains
___

### Q: Which ERC20 tokens do you expect will interact with the smart contracts? 
ETHx (Superfluid Super ETH) within the auction & beneficiary distribution
___

### Q: Which ERC721 tokens do you expect will interact with the smart contracts? 
Any (via the wrapping functionality); A "PCOArt-modified" ERC721 token is created in minting and ownership (Stewardship) is controlled by the auction/PCO logic.
___

### Q: Do you plan to support ERC1155?
Any (via the wrapping functionality)--becomes a PCOArt-modified ERC721
___

### Q: Which ERC777 tokens do you expect will interact with the smart contracts? 
None
___

### Q: Are there any FEE-ON-TRANSFER tokens interacting with the smart contracts?

No
___

### Q: Are there any REBASING tokens interacting with the smart contracts?

No
___

### Q: Are the admins of the protocols your contracts integrate with (if any) TRUSTED or RESTRICTED?
RESTRICTED
___

### Q: Is the admin/owner of the protocol/contracts TRUSTED or RESTRICTED?
TRUSTED - The collection owner (`owner` in `OwnableDiamond`) can swap out Diamond facet contracts resulting in changes to or entirely circumventing the core PCO functionality and flow of funds.
___

### Q: Are there any additional protocol roles? If yes, please explain in detail:
- Role Admin (DEFAULT_ADMIN_ROLE) - can change the address(es) assigned to the "Component Roles" that follow.
- PCO Settings Admin (PeriodicPCOParamsFacet.COMPONENT_ROLE) - can change the Stewardship Cycle Duration and the Honorarium Rate, but cannot swap out the PCO facet contract. Changes take effect in the next Stewardship Cycle/Auction Pitch.
- Auction Pitch Admin (EnglishPeriodicAuctionFacet.COMPONENT_ROLE) - can change all attributes of the collection's Auction Pitches (except for the initial auction date), but cannot swap out the auction facet contract. Changes will take immediate effect including if an auction is in progress.
- Auction Pitch Eligibility Admin (AllowlistFacet.COMPONENT_ROLE) - can flip between open or closed eligibility and update the eligible addresses, but cannot swap out the allowlist facet contract. Changes will take immediate effect.
- Creator Circle Admin (IDABeneficiaryFacet.COMPONENT_ROLE) - can change beneficiary group membership units including removing/adding members, but cannot swap out the beneficiary facet contract. Changes will take effect when the next auction is closed.
- Mint Additional Tokens Admin (ADD_TOKEN_TO_COLLECTION_ROLE) - can add new tokens to a collection after the initial creation event.

https://pco-art-docs.vercel.app/for-artists/admin-permissions
___

### Q: Is the code/contract expected to comply with any EIPs? Are there specific assumptions around adhering to those EIPs that Watsons should be aware of?
ERC-2535. N/A EIPs
___

### Q: Please list any known issues/acceptable risks that should not result in a valid finding.
ERC721/1155 tokens with alternative methods for changing the token owner aren't suitable for wrapping into PCOArt NFTs. If the artist chooses to maintain or grant the `owner` role of the collection's `OwnableDimond`, this address becomes TRUSTED and maintains broad abilities to alter the core functionality of the PCOArt collection.
___

### Q: Please provide links to previous audits (if any).
N/A
___

### Q: Are there any off-chain mechanisms or off-chain procedures for the protocol (keeper bots, input validation expectations, etc)?
No
___

### Q: In case of external protocol integrations, are the risks of external contracts pausing or executing an emergency withdrawal acceptable? If not, Watsons will submit issues related to these situations that can harm your protocol's functionality.
No
___

### Q: Do you expect to use any of the following tokens with non-standard behaviour with the smart contracts?
No
___

### Q: Add links to relevant protocol resources
- https://pco-art-docs.vercel.app/
- https://github.com/RadicalxChange/pco-art/blob/main/hardhat.config.ts
- https://github.com/RadicalxChange/pco-art/blob/main/flake.nix
- https://github.com/RadicalxChange/pco-art/blob/main/CHANGELOG.md
- https://github.com/RadicalxChange/pco-art/blob/main/README.md
___



# Audit scope


[pco-art @ 4acd6b06840028ba616b6200439ce0d6aa1e6276](https://github.com/RadicalxChange/pco-art/tree/4acd6b06840028ba616b6200439ce0d6aa1e6276)
- [pco-art/contracts/auction/EnglishPeriodicAuctionInternal.sol](pco-art/contracts/auction/EnglishPeriodicAuctionInternal.sol)
- [pco-art/contracts/auction/EnglishPeriodicAuctionStorage.sol](pco-art/contracts/auction/EnglishPeriodicAuctionStorage.sol)
- [pco-art/contracts/auction/IEnglishPeriodicAuctionInternal.sol](pco-art/contracts/auction/IEnglishPeriodicAuctionInternal.sol)
- [pco-art/contracts/auction/IPeriodicAuctionReadable.sol](pco-art/contracts/auction/IPeriodicAuctionReadable.sol)
- [pco-art/contracts/auction/IPeriodicAuctionWritable.sol](pco-art/contracts/auction/IPeriodicAuctionWritable.sol)
- [pco-art/contracts/auction/facets/EnglishPeriodicAuctionFacet.sol](pco-art/contracts/auction/facets/EnglishPeriodicAuctionFacet.sol)


