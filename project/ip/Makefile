all: pipework_altera.vhd

pipework_altera.vhd :
	../../FPGA-SoC-Linux-Example-1-Base/PUMP_AXI4/PipeWork/tools/vhdl-archiver.rb -v  \
            --library PipeWork                                          \
            --use 'SDPRAM(ALTERA_AUTO_SELECT)'                          \
            --use 'QUEUE_ARBITER(INTEGER_ARCH)'                         \
            --archive pipework_altera.vhd                               \
            ../../FPGA-SoC-Linux-Example-1-Base/PUMP_AXI4/PipeWork/src/ \
	    --library work                                              \
	    --top LED8_AXI                                              \
	    --top PUMP_AXI3_TO_AXI3                                     \
	    ./ikwzm_pipework_led8_axi_0.1/                              \
	    ./ikwzm_pipework_pump_axi_to_axi_1.0/                       \
	    $(ENDLIST)

