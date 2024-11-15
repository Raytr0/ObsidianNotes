#### **Attempt 1**
![[Pasted image 20241114112357.png]]
1. **Customer Management**:
    - Classes: `Customer`, `Account`, `Debit Card`
2. **Bank Operations**:
    - Classes: `Bank`, `ATM`, `ATM Transactions`
3. **Transaction Processing**:
    - Classes: `Withdrawal`, `Transfer`, `Pin Generation`
4. **Account Management**:
    - Classes: `Savings Account`, `Current Account`

#### **Attempt 2**
![[Pasted image 20241114114006.png]]
1. **Account Component**:
    - Classes: `ATM Transactions`,`Account`, `Savings Account`, `Current Account`
2. **Bank Component**:
    - Classes: `Bank`, `ATM`,`Debit Card`, `Customer`
3. **ATM Component**:
    - Classes: `Withdrawal`, `Transfer`, `Pin Generation`

Task 2:
Git (Repository)
![[Pasted image 20241115133150.png]]
classes/entities:
	Repository
	Commit
	Branch
	User
	CommitHistory
	Tag
	Merge
	Organization
Components/Subsystem:
	Repository Management
		Tag, Branch, Commit
	User Management
		User, Organization
	Repository Storage
		Repository, CommitHistory

BitTorrent(Peer to Peer)
![[Pasted image 20241115133611.png]]
classes/entities:
	Client
	Peer
	Session
	File
	Connect
Components/Subsystem:
Session Management:
	Session, Client, Connect
Data Transfer:
	Peer, File

Online Bank(Client Server)
![[Pasted image 20241115134240.png]]
Classes/entities:
	Customer
	Profile
	Bank
	Account
	Savings Account
	Checking Account
	Transaction
	Card
	Notification
Components/Subsystem:
	Bank Management:
		Bank, Customer
	User Management:
		Profile, Account
	Account Management:
		Savings Account, Checking Account
	Card Management:
		Card
	Transactions:
		Transaction, Notification