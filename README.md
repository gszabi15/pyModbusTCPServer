```
import server, threading

# Modbus slave setup
c = server.ModbusServer(host="0.0.0.0", port=502) #  (host="localhost", port=const.MODBUS_PORT, no_block=False, ipv6=False) -> None    const.MODBUS_PORT=502 default
threading._start_new_thread(c.start, ())

# set data
server.DataBank.set_input_registers(0,[200]) # (address, word_list) -> Literal[True] | None

server.DataBank.set_holding_registers(1,[100]) # (address, word_list) -> Literal[True] | None

server.DataBank.set_discrete_inputs(2, [True]) # (address, bit_list) -> Literal[True] | None

server.DataBank.set_coils(3,[True]) # (address, bit_list) -> Literal[True] | None


# read data
print(server.DataBank.get_input_registers(0,1)) # (address, number=1) -> list[int] | None

print(server.DataBank.get_holding_registers(1,1)) # (address, number=1) -> list[int] | None

print(server.DataBank.get_discrete_inputs(2,1)) # (address, number=1) -> list[bool] | None

print(server.DataBank.get_coils(3,1)) # (address, number=1) -> list[bool] | None


while 1:
    pass
```
