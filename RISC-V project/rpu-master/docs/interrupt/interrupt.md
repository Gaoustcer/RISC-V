1.文件中有一个中断控制器int_controller，开始时处于IDLE状态。如果此时有外部中断输入且允许中断，则中断控制器进入PENDING状态并输出中断的id与irq_sec_i(？)。
   此时若控制器controller处于decode状态，且不在debug状态时，控制器会进入IRQ_FLUSH状态并且发出信号阻塞if与id。
      a.在IRQ_FLUSH中如果PMP访问内存出错（data_error load & store），此时控制器向csr发出信号保存ex内容，并且进入FLUSH_WB。FLUSH_WB中会发出信号阻塞if和id，并保护现场（？），在没有非法指令（？）的情况下会回到DECODE阶段
      b.如果PMP未发出data_error,且有中断请求，则会进入IRQ_TAKEN_ID中。
      c.IRQ_TAKEN_ID会向crs发出各种控制信号（包括保存id信息），处理完成后会回到DECODE
   若控制器处于FIRST_FETCH（boot状态后开始取第一条指令）并且收到中断请求，则会阻塞if，id并进入IRQ_TAKEN_IF状态。
      a.IRQ_TAKEN_IF中除了保存if信息外其他信号与IRQ_TAKEN_ID相同
2.控制器controller在DECODE阶段如果既没有中断也没有debug时，如果碰到了非法指令则会进入FLUSH_EX阶段
   FLUSH_EX中，控制器发出信号阻塞if，id，
      a.data_error时向csr发出信号保存ex信息，并准备进入FLUSH_WB
      b.否则，等到EX右边的流水段完成之后再进入FLUSH_WB阶段