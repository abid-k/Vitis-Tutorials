#
#Copyright 2020 Xilinx, Inc.
#Licensed under the Apache License, Version 2.0 (the "License");
#you may not use this file except in compliance with the License.
#You may obtain a copy of the License at
#    http://www.apache.org/licenses/LICENSE-2.0
#Unless required by applicable law or agreed to in writing, software
#distributed under the License is distributed on an "AS IS" BASIS,
#WITHOUT WARRANTIES OR CONDITIONS OF ANY KIND, either express or implied.
#See the License for the specific language governing permissions and
#limitations under the License.
#
TARGET   = hw
MODE	 = linux
PLATFORM = ${PLATFORM_REPO_PATHS}/xilinx_vck190_es1_base_202020_1/xilinx_vck190_es1_base_202020_1.xpfm
XPFM	 = vck190_xpfm
ROOTFS   = ${PLATFORM_REPO_PATHS}/sw/versal/xilinx-versal-common-v2020.2/rootfs.ext4 
IMAGE    = ${PLATFORM_REPO_PATHS}/sw/versal/xilinx-versal-common-v2020.2/Image 

GRAPH    = aie/graph.cpp
LIBADF  = libadf.a
AIE_CMPL_CMD = aiecompiler -platform=${PLATFORM} -include="./aie" -workdir=./Work ${GRAPH}
AIE_SIM_CMD = aiesimulator --pkg-dir=./Work --dump-vcd foo

##########################################################################################################################################################
### DO NOT MODIFY BELOW THIS LINE UNLESS NECESSARY
################################################################################################################################################

.PHONY: clean

aie: ${LIBADF}
${LIBADF}: aie/*
	${AIE_CMPL_CMD}

aiesim: ${LIBADF}
	${AIE_SIM_CMD}

clean:
	rm -rf _x v++_* ${XOS} ${OS} ${LIBADF} *.o.* *.o *.xpe *.xo.* \
	       vck190_aie_base*.xclbin* *.xsa *.log *.jou xnwOut Work Map_Report.csv \
	       ilpProblem* sol.db drivers .Xil
	make -C sw clean
