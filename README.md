# learn-metacrafters-1
I upload my learning journey with Metacrafters here.
# Project: Create a Token
This is my entry for our project in Metacrafters dealing with token creation in the blockchain
For this project we are tasked to create a token that will fulfill the following requirements:
1. Your contract will have public variables that store the details about your coin (Token Name, Token Abbrv., Total Supply)
2. Your contract will have a mapping of addresses to balances (address => uint)
3. You will have a mint function that takes two parameters: an address and a value. The function then increases the total supply by that number and increases the balance of the address by that amount.
4. Your contract will have a burn function, which works the opposite of the mint function, as it will destroy tokens. It will take an address and value just like the mint functions. It will then deduct the value from the total supply and from the balance of the address.
5. Lastly, your burn function should have conditionals to make sure the balance of account is greater than or equal to the amount that is supposed to be burned.
# Public Variables
    string public n; // name
    string public s; // synbol
    uint256 public tS; // total supply
# Mapping Variables 
    mapping(address => uint256) public balanceOf;
    event Mint(address indexed to, uint256 val);
    event Burn(address indexed from, uint256 val);
I utilized the use of event keyword to notify external entities regarding specific occurences within the transaction
# Mint Function
    function mint(address _to, uint256 _val) public 
    {
      tS = tS + _val;
      balanceOf[_to] = balanceOf[_to] + _val;
      emit Mint(_to, _val);
    }
I utilized the use of emit keyword as a way to log the transactions happening to and from the wallet address
# Burn Function
    function burn(address _from, uint256 _val) public 
    {
        require(balanceOf[_from] >= _val, "Error! Insufficient balance");
        
        tS = tS - _val;
        balanceOf[_from] = balanceOf[_from] - _val;
        emit Burn(_from, _val);
    }
# Conditional Statement
       require(balanceOf[_from] >= _val, "Error! Insufficient balance");
To check whether the transaction is valid by ensuring that the balance is always sufficient
