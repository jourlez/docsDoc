---
sidebar_position: 3
---

# Functions


Annotations

Callable Functions

Built-in Functions

## Account Data Storage Functions

### getBinary(Address|Alias, String): ByteVector|Unit

### getBinary(String): ByteVector|Unit

### getBinaryValue(Address|Alias, String): ByteVector

### getBinaryValue(String): ByteVector

### getBoolean(Address|Alias, String): Boolean|Unit

### getBoolean(String): Boolean|Unit

### getBooleanValue(Address|Alias, String): Boolean

### getBooleanValue(String): Boolean

### getInteger(Address|Alias, String): Int|Unit

### getInteger(String): Int|Unit

### getIntegerValue(Address|Alias, String): Int

### getIntegerValue(String): Int

### getString(Address|Alias, String): String|Unit

### getString(String): String|Unit

### getStringValue(Address|Alias, String): String

### getStringValue(String): String

### isDataStorageUntouched(Address|Alias): Boolean

## Blockchain Functions

### addressFromRecipient(Address|Alias): Address

### assetBalance(Address|Alias, ByteVector): Int

### assetInfo(ByteVector): Asset|Unit	

### blockInfoByHeight(Int): BlockInfo |Unit	

### calculateAssetId(Issue): ByteVector

### calculateLeaseId(Lease): ByteVector

### scriptHash(Address|Alias): ByteVector|Unit

### transactionHeightById(ByteVector): Int|Unit

### transferTransactionById(ByteVector): TransferTransaction|Unit

### decentralcoinBalance(Address|Alias): BalanceDetails

## Byte Array Functions

### drop(ByteVector, Int): ByteVector	

### dropRight(ByteVector, Int): ByteVector 

### size(ByteVector): Int

### take(ByteVector, Int): ByteVector

### takeRight(ByteVector, Int): ByteVector

## Converting Functions

### addressFromPublicKey(ByteVector): Address

### parseBigInt(String): BigInt|Unit

### parseBigIntValue(String): BigInt

### parseInt(String): Int|Unit

### parseIntValue(String): Int

### toBigInt(ByteVector): BigInt

### toBigInt(ByteVector, Int, Int): BigInt

### toBigInt(Int): BigInt

### toBytes(Boolean): ByteVector

### toBytes(Int): ByteVector

### toBytes(String): ByteVector	

### toBytes(BigInt): ByteVector

### toInt(BigInt): Int

### toInt(ByteVector): Int	

### toInt(ByteVector, Int): Int

### toString(Address): String

### toString(Boolean): String

### toString(Int): String

### toString(BigInt): String

### toUtf8String(ByteVector): String

### transferTransactionFromProto(ByteVector): TransferTransaction|Unit


## dApp-to-dApp Invocation Function

### invoke

### reentrantInvoke

## Data Transaction Functions

### getBinary(List[], String): ByteVector|Unit

### getBinary(List[], Int): ByteVector|Unit

### getBinaryValue(List[], String): ByteVector

### getBinaryValue(List[], Int): ByteVector

### getBoolean(List[], String): Boolean|Unit	

### getBoolean(List[], Int): Boolean|Unit

### getBooleanValue(List[], String): Boolean

### getBooleanValue(List[], Int: Boolean

### getInteger(List[], String): Int|Unit

### getInteger(List[], Int): Int|Unit

### getIntegerValue(List[], String): Int

### getIntegerValue(List[], Int): Int

### getString(List[] String): String|Unit

### getString(List[], Int): String|Unit

### getStringValue(List[], String): String

### getStringValue(List[], Int): String

## Decoding Functions

### addressFromString(String): Address|Unit

### addressFromStringValue(String): Address

### fromBase16String(String): ByteVector	

### fromBase58String(String): ByteVector

### fromBase64String(String): ByteVector

## Encoding Functions

### toBase16String(ByteVector): String

### toBase58String(ByteVector): String

### toBase64String(ByteVector): String

## Exception Functions

### throw()

### throw(String)

## Hashing Functions

### blake2b256

### keccak256

### sha256

## List Functions

### cons(A, List[B]): List[A|B]	

### containsElement(List[T], T): Boolean

### getElement(List[T], Int): T	

### indexOf(List[T], T): Int|Unit

### lastIndexOf(List[T], T): Int|Unit

### max(List[Int]): Int

### max(List[BigInt]): BigInt

### min(List[Int]): Int

### min(List[BigInt]): BigInt

### removeByIndex(List[T], Int): List[T]

### size(List[T]): Int

## Math Functions

### fraction(Int, Int, Int): Int

### fraction(Int, Int, Int, Union): Int

### fraction(BigInt, BigInt, BigInt): BigInt

### fraction(BigInt, BigInt, BigInt, Union): BigInt

### log(Int, Int, Int, Int, Int, Union): Int

### log(BigInt, Int, BigInt, Int, Int, Union): BigInt

### median(List[Int]): Int

### median(List[BigInt]): BigInt

### pow(Int, Int, Int, Int, Int, Union): Int

### pow(BigInt, Int, BigInt, Int, Int, Union): BigInt

### sqrt(Int, Int, Int, Union): Int

### sqrt(BigInt, Int, Int, Union): BigInt

## String Functions

### contains(String, String): Boolean

### drop(String, Int): String

### dropRight(String, Int): String

### indexOf(String, String): Int|Unit

### indexOf(String, String, Int): Int|Unit

### lastIndexOf(String, String): Int|Unit

### lastindexOf(String, String, Int): Int|Unit

### makeString(List[String], String): String

### size(String): Int

### split(String, String): List[String]

### take(String, Int): String	

### takeRight(String, Int): String

## Union Functions

### isDefined(T|Unit): Boolean

### value(T|Unit): T

### valueOrElse(T|Unit, T): T

### valueOrErrorMessage(T|Unit, String): T

## Verification Functions

### bn256Groth16Verify

### createMerkleRoot

### ecrecover

### groth16Verify

### rsaVerify

### sigVerify