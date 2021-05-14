# Blockchain

## Steps for creating a custom network and perform transactions locally

### Step 1 - Setting up the accounts
To setup the accounts, navigate to folder where you have installed GET tools on terminal(MAC) and run the following commands, please make sure to save the public keys. You will also need to set the passwords to secure your wallets.
- ./geth --datadir node1 account new
- ./geth --datadir node2 account new

After this, you will see two folders for the above will be created in your directory:
![image](https://user-images.githubusercontent.com/74744286/118044184-562efc80-b344-11eb-8276-4736c3f59889.png)

### Step 2- Setting up the network

After creating accounts, run the command PUPPETH:
![image](https://user-images.githubusercontent.com/74744286/118045469-efaade00-b345-11eb-9a15-a9b5a5da7341.png)

- Configration:
  - Choose the Clique (Proof of Authority) consensus algorithm
  - Paste both account addresses from the first step one at a time into the list of accounts to seal
  - Paste them again in the list of accounts to pre-fund
  - Choose no for pre-funding 
  - Complete the rest of the prompts, and when you are back at the main menu, choose the "Manage existing genesis" option
  - Export genesis configurations
 ![image](https://user-images.githubusercontent.com/74744286/118047183-677a0800-b348-11eb-86d1-0de93f40f366.png)
 
 Now we to intialize each node for minnig by running the following in terminal:
 - ./geth --datadir node1 init yournetworkname.json
 - ./geth --datadir node2 init yournetworkname.json
 
 To start the minning, run the following in seperate terminals:
 - ./geth --datadir node1 --unlock "ACCOUNT_ONE_ADDRESS" --mine --rpc --allow-insecure-unlock. Please copy the encode after running it:
   ![image](https://user-images.githubusercontent.com/74744286/118048024-a78dba80-b349-11eb-953d-156676b8425a.png)

 - For the second account : ./geth --datadir node2 --unlock "ACCOUNT_TWO_ADDRESS" --mine --port 30304 --bootnodes "enode address that was     copied from account 1" --ipcdisable --allow-insecure-unlock.  Encode is used to link them.
 
 When you run both of the commands, mining should be started:
 ![image](https://user-images.githubusercontent.com/74744286/118048562-71046f80-b34a-11eb-97a1-25b8e25ebdf4.png)
 
 ### STEP3- Adding your network to MYCRYPTO app:
 
 - Open the MyCrypto app, then click Change Network at the bottom left:
   ![image](https://user-images.githubusercontent.com/74744286/118049446-bf663e00-b34b-11eb-860e-4ad0ba217109.png)
   
 - Click "Add Custom Node", then add the custom network information that you set in the genesis
   [image](https://user-images.githubusercontent.com/74744286/118049841-53d0a080-b34c-11eb-89e7-06b3286dd6b2.png)
 - Type ETH in the Currency box
 - In the Chain ID box, type the chain id you generated during genesis creation. Mine is 745 as hown above
 - In the URL box type: http://127.0.0.1:8545.  This points to the default RPC port on your local machine
 - Finally, click Save & Use Custom Node

### STEP4, Perform a transcation between the two accounts:
 - Select the View & Send option from the left menu pane, then click Keystore file
 ![image](https://user-images.githubusercontent.com/74744286/118050324-07399500-b34d-11eb-92f9-bd82d5b448c3.png)
 - Select Wallet File, then navigate to the keystore directory inside your Node1 directory:
  ![image](https://user-images.githubusercontent.com/74744286/118050514-6b5c5900-b34d-11eb-8013-ed13dbf6f029.png)
 - This will open your account wallet inside MyCrypto.
 - To send ETH to account 2, in the To Address box, type the account address from Node2, then fill in an arbitrary amount of ETH to send and click on send transaction.
   ![image](https://user-images.githubusercontent.com/74744286/118050827-03f2d900-b34e-11eb-8829-3e063bea0234.png)
   ![image](https://user-images.githubusercontent.com/74744286/118050932-2c7ad300-b34e-11eb-9703-39185f81f7d4.png)
   ![image](https://user-images.githubusercontent.com/74744286/118051021-4b796500-b34e-11eb-9547-0e3d1814f249.png)
 - Click the Check TX Status when the green message pops up, confirm the logout:
   ![image](https://user-images.githubusercontent.com/74744286/118051367-deb29a80-b34e-11eb-8fe0-4c2d49fb1073.png)
 - You should see the transaction go from Pending to Successful in around the same blocktime you set in the genesis. For me, I am sending a large amount and per blocktime is also high, due to which it is taking long time.
 - You can click the Check TX Status button to update the status.

Thank you
  

 



   

   


 
 
 


