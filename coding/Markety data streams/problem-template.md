# Write your solution here.
# Python version 3.12.3
## All the packages you need to complete this problem are already installed
## for you in our local (sandbox) virtual environment.

from dataclasses import dataclass
from enum import Enum, auto


type Quantity = int
type Price = float
type SeqNo = int


# DO NOT MODIFY
class Event(Enum):
    DISCONNECT = auto()
    ADD = auto()
    CHANGE = auto()
    DELETE = auto()

# DO NOT ADD OR DELETE ANY DATACLASS FIELDS
@dataclass
class DataBlock:
    event: Event 
    price: Price | None
    quantity: Quantity | None
    seqNo: SeqNo
    isBuy: bool | None
    

@dataclass
class OrderBook:
    bids: dict[Price, Quantity]
    asks: dict[Price, Quantity]
    
@dataclass
class Snapshot:
    book: OrderBook
    asOfSeqNo: SeqNo

class EventStream:
    def __init__(self):
        self.orderBook: OrderBook = OrderBook({}, {})
    

    # Implement this
    def processMessage(self, msg: DataBlock | Snapshot) -> None:
        pass