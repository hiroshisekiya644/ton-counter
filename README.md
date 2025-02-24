# TON Counter Smart Contract

This is a simple TON smart contract designed to manage and increase a counter. The contract supports a basic "increase" operation and provides methods for querying the current counter value and the context ID.

## Features

- **Counter Management**: The contract allows the counter value to be increased by a specified amount.
- **Context ID**: Each contract instance has a unique `ctx_id` that helps to differentiate it from others.
- **Get Methods**: External queries can retrieve the current value of the counter and the context ID.
- **Error Handling**: The contract bounces invalid messages back to the sender, providing clear error feedback.

## Contract Functions

- **`load_data()`**: Loads the contract's internal state, including `ctx_id` and `ctx_counter`, from storage.
- **`save_data()`**: Saves the current state (`ctx_id` and `ctx_counter`) back to persistent storage.
- **`recv_internal(int my_balance, int msg_value, cell in_msg_full, slice in_msg_body)`**: Handles incoming messages. It processes the "increase" operation and handles invalid operations with errors.
- **`get_counter()`**: A getter method that returns the current value of the counter.
- **`get_id()`**: A getter method that returns the context ID of the contract.

## Operations

### `op::increase`

The contract supports one operation: `op::increase`, which increments the counter by a specified value. The message format for this operation is as follows:

- **op (32 bits)**: The operation code (in this case, `op::increase`).
- **increase_by (32 bits)**: The amount by which the counter should be increased.

### Example of Usage

1. **Deploy the Contract**: When deploying the contract, initialize it with a unique `ctx_id` and a starting counter value.
2. **Send the Increase Operation**:
   - Send a message with the `op::increase` operation and the desired increment value.
   - The contract will increase the counter accordingly.
3. **Query the Counter**:
   - Use the `get_counter()` method to retrieve the current counter value.
   - Use the `get_id()` method to retrieve the unique `ctx_id`.

### License

This contract is open-source and available under the [MIT License](LICENSE).
