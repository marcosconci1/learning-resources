# Implement a FeedHandler

You're building a component responsible for processing incoming market data messages and maintaining an up-to-date orderbook. The event stream begins with an initial snapshot of the market, followed by incremental updates represented by data blocks.

Each `DataBlock` contains an event type and relevant fields depending on that event.

## Supported Event Types
The four supported event types are:

*   **ADD**: Insert a new price level with the specified quantity.
*   **CHANGE**: Modify the quantity at an existing price level.
*   **DELETE**: Remove an existing price level from the book.
*   **DISCONNECT**: Clear the current `OrderBook` and mark the connection as inactive.

Any data blocks received while disconnected should not change the book. Instead, if a new snapshot is sent while disconnected, you must rebuild the book using that snapshot and apply any events whose `DataBlock` have a `seqNo` later than the snapshot's `asOfSeqNo`. It will be guaranteed that the `asOfSeqNo` is greater than or equal to the last `DISCONNECT` `seqNo`.

---

## Requirements

### DataBlock
*   `DataBlocks` must be processed sequentially (by `seqNo`) but are not guaranteed to be sent in order. This includes when the event stream is disconnected.
*   The first block to be processed will always have a sequence number of 1, and the next one should have one of 2.
*   `ADD`, `CHANGE`, and `DELETE` will affect **bids** if `isBuy` is `True`.
*   `ADD`, `CHANGE`, and `DELETE` will affect **asks** if `isBuy` is `False`.
*   `CHANGE` events can have a negative quantity.
*   `DELETE` events will have a value of `None` for their quantity.
*   `DISCONNECT` events will have a value of `None` for their price, quantity, and `isBuy`.

### Snapshot
*   Snapshots are always sent in order.
*   Snapshots can only be sent at the start or after a `DISCONNECT`.
*   A `Snapshot` is always sent at the start with a `asOfSeqNo` of 1.
*   You may want to add methods to them and you are free to do so.

---

## Evaluation

### Test Descriptions
*   **testAddEvent**: Single `ADD` `DataBlock`
*   **testChangeEvent**: Single `CHANGE` `DataBlock`
*   **testDeleteEvent**: Single `DELETE` `DataBlock`
*   **testAllEvents**: All possible `DataBlock` events besides `DISCONNECT`
*   **testDisconnect**: Multiple `DataBlock`s, a `DISCONNECT` event, multiple lost `DataBlock`s, and then a `Snapshot`
*   **testOutOfOrderEvents**: Multiple `DataBlock` events besides `DISCONNECT` received out of order.
*   **testOutOfOrderLostMessages**: Multiple `DataBlock`s after a `DISCONNECT` received out of order
*   **testMultipleDisconnects**: Multiple `DISCONNECT` `DataBlock`s received out of order

---

## Notes
*   You can assume any `DataBlock` event is valid. For example, if we try to process a `DELETE` `DataBlock` the specified price will exist.
*   You should not add or modify any of the fields in `DataBlock`, `OrderBook`, and `Snapshot`. If you want to add methods to them, you are free to do so.
*   Upon a `DISCONNECT` event, only clear the existing `OrderBook`. `DataBlock`s received whose `seqNo` occur after the `DISCONNECT` should still be processed in sequence.
*   You should aim to outperform brute force search on an iterable whenever possible.

---

## Use Cases

### Case 1: Standard Flow
```
eventStream = EventStream() 
snapShot_1 = Snapshot(OrderBook({1:2}, {5:3}), 1) 
dataBlock_1 = DataBlock(Event.ADD, 2, 5, 1, True) 
dataBlock_2 = DataBlock(Event.DELETE, 5, None, 2, False) 

e.processMessage(snapShot_1)   # As of SeqNo 1 
e.processMessage(datablock_1)  # SeqNo 1 
e.processMessage(datablock_2)  # SeqNo 2 

# Final OrderBook = Bids: {1:2, 2:5}, Asks: {}
```

### Case 2: Disconnect & Out of Order
```
eventStream = EventStream() 
snapShot_1 = Snapshot(OrderBook({1:2}, {5:3}), 1) 
dataBlock_1 = DataBlock(Event.DISCONNECT, None, None, 1, None) 
dataBlock_2 = DataBlock(Event.CHANGE, 5, 5, 3, True) 
dataBlock_3 = DataBlock(Event.CHANGE, 7, -2, 2, False) 
snapShot_2 = Snapshot(OrderBook({5:2}, {7:3}), 2) 

e.processMessage(Snapshot_1)   # As of SeqNo 1 
e.processMessage(dataBlock_1)  # SeqNo 1 
e.processMessage(dataBlock_2)  # SeqNo 3 
e.processMessage(dataBlock_3)  # SeqNo 2 
e.processMessage(snapShot_2)   # As of SeqNo 2 

# Final OrderBook = Bids: {5:5}, Asks: {7:3}
```

---

## Uncook me! (Hints)
*   In what situations would we have to store a datablock for later?
*   What type of data structure can be used to store and retrieve datablocks efficiently?
*   You can use recursion to process a stored `DataBlock` after receiving a relevant `DataBlock` or a `Snapshot`.

# Source
https://getcracked.io/problem/16/markety-data-streams
