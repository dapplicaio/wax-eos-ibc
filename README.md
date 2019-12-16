# wax-eos-ibc
WAX-EOS Inter Blockchain Communiction framework



1. A WAX account (user's source account) transfers tokens to WAX IBC contract specifying target chain (EOS) and account

2. WAX IBC Contract verifies the transaction for validity of parameters and creates a record in its table with a status new

3. WAX IBC Oracle checks for new records, generates signature with its private key, updates the record with the signature, sets status to ready

4.1, 4.2 Gate IBC Oracle reads the 'ready' record and creates the trx request in EOS-WAX IBC contract (via corresponding action call)

5. 6. EOS-WAX IBC contract verifies the request's signature (using corresponding pub_key), and executes the transfer, updates status of the record to executed.

7. EOS IBC Oracle generates signature for the executed records and updates its status to confirmed.

8.1 8.2. Gate IBC Oracle reads the confirmed record along w/ trx's signature proof and calls a corresponding action of WAX IBC contract

9. WAX IBC contract verifies the requests parameters,and updates the records as complete. 

10. [Optional] Token/Asset owner at WAX chain, checks for complete actions and burns/ or locks the corresponding amounts.

11. [Optional] Token/Asset owner at EOS checks for complete actions by EOS WAX IBC Contract and mints/ or unlocks the corresponding amounts.
