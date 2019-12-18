# APB Timer

This unit provides a simple timer via the APB bus.
It supports an arbitrary number of 32-bit wide timers. Each timer has three
registers, the timer register, the timer compare register and the timer control
register.

## register

| name           | address | access | details                                                      |
| -------------- | ------- | ------ | ------------------------------------------------------------ |
| REG_TIMER      | 0x00    | W/R    | Count up from set value to `0xffff_ffff`, when the value reaches `0xffff_ffff`, the `irq_o[0]` port will be set high and the `REG_TIMER`  will be set to `0`. |
| REG_TIMER_CTRL | 0x04    | W/R    | The `bit 0` is `ENABLE_BIT`, the `bit 3` is `PRESCALER_STARTBIT`, the `bit 5` is `PRESCALER_STOPBIT`, when `ENABLE_BIT` is set, timer run on normal count mode. |
| REG_CMP        | 0x08    | W/R    | The `REG_TIMER` will be reset to `0` if compare register is written. If `REG_CMP` is not equal to `0` and `REG_TIMER` is equal to `REG_CMP`, the `irq_o[1]` port will be set high and the `REG_TIMER`  will be set to `0`. |

