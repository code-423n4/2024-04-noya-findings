# [I-1] TITLE Informational Findings

***Description:***

The NoyaFeeReciever contract should use Ownable2Step instead of Ownable

**Impact:**
This is technically not a vulnerablity , but openZeppelin Ownable can lead to loss of contract ownership if ownership is transferred to a non-existent address. Ownable2step requires the reciever o confirm ownership. this insures against accidentally sending ownership to a mistyped address 
