# Ethereum Lottery Smart Contract
Smart Contract that sells tickets for lottery and draws winner for each step of lottery.

### How it works?
1.Lottery starts with 1000 (threshold)
  buy, buy with referral, buy bulk tickets are availble
  tickets are identified and indexed by ticket number
  ticket numbers are sold tickets, increasing as time being
  each ticket have holder's address, ref ticket number, winning Amount and paid flag(boolean)
  check ref number is valid
2.Once soldTickets reached to threshold, draw randomly a winner
  pick a random number between (start, start + threshold)
  distribute winning amount & house edge, referral share amount
  and add amounts in each wallet (indexed by address)
  house edge will be sent directly to owner of contract
  # there is an option to draw lottery manually by admin
3.Once drawn winner, next step starts
  as we discussed; 1000, 10k, ..., 10M, next 1000
4.Users can withdraw with withdraw address, and ticket number
  we check following;
    - valid address
    - msg.sender is the holder of the ticket
    - check the ticket was already paid
    - check the ticket is winning ticket and wallet balance is enough
  send ticket winning amount to withdraw address, update ticket as paid, and subtract wallet balance  
5.Users can withdraw all balances 
6.Users can check winning ticket of last lottery
7.Users can check his purchased ticket info
8.Users can check his balance

### Admin functions
1. Admin can set house edge
2. Admin can set ticket price
3. Admin can set referral share
4. Admin can pause/resume lottery
5. Admin can destroy contract anytime
