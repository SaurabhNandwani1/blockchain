# blockchain
BlockChain
sudo apt-get update
    sudo apt-get install -y ca-certificates curl gnupg
    sudo mkdir -p /etc/apt/keyrings
    curl -fsSL https://deb.nodesource.com/gpgkey/nodesource-repo.gpg.key | sudo gpg --dearmor -o /etc/apt/keyrings/nodesource.gpg
    NODE_MAJOR=20
    echo "deb [signed-by=/etc/apt/keyrings/nodesource.gpg] https://deb.nodesource.com/node_$NODE_MAJOR.x nodistro main" | sudo tee /etc/apt/sources.list.d/nodesource.list
    sudo apt-get update
    sudo apt-get install nodejs -y
    npm install web3
    npm install --save-dev @nomiclabs/hardhat-ethers ethers @nomiclabs/hardhat-waffle ethereum-waffle chai
   
mkdir test
cd test
npx hardhat init
cd contract
vi Hello.sol

pragma solidity ^0.8.9;

// Store a single data point and allow fetching/updating of that datapoint
contract Hello {

    // data point
    string public storedData;

    event myEventTest(string eventOutput);

    function set(string memory myText) public {
        storedData = myText;
        emit myEventTest(myText);
    }

    function get() public view returns (string memory) {
        return storedData;
    }

}



npx hardhat node --hostname localhost    # make sure to run as localhost vs the dns


npx hardhat console --network localhost




e.g.
>await ethers.provider.getBalance("0xf39Fd6e51aad88F6F4ce6aB8827279cffFb92266")


e.g.
> await ethers.provider.getBalance("0x71A3Bfe8f5d56F42B39F3f218edCac6311B2f38f")
845744216400112038531n


npx hardhat console --network localhost
Welcome to Node.js v14.21.3.
Type ".help" for more information.
>  const signers = await ethers.getSigners();
undefined
> const contract =  await ethers.getContractFactory("Hello")
undefined
>const bal = await ethers.provider.getBalance(signers[0])
> const cd = await contract.deploy()
> const bal2 = await ethers.provider.getBalance(signers[0])
undefined
> bal2
9999990092056610771200n
> await cd.set('aaabbbb')
Promise {
  <pending>,
  [Symbol(async_id_symbol)]: 3248,
  [Symbol(trigger_async_id_symbol)]: 13,
  [Symbol(destroyed)]: { destroyed: false }
}
> await cd.get()
'aaabbbb'
>const bal2 = await ethers.provider.getBalance(signers[0])
>bal
