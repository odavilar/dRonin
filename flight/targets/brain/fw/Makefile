###############################################################################
# @file       Makefile
# @author     The OpenPilot Team, http://www.openpilot.org, Copyright (C) 2009.
# @author     Tau Labs, http://taulabs.org, Copyright (C) 2012-2013
# @author     dRonin, http://dronin.org Copyright (C) 2015-2016
#
# @addtogroup
# @{
# @addtogroup
# @{
# @brief Makefile to build firmware for the FlyingF4 board.
###############################################################################
#
# This program is free software; you can redistribute it and/or modify
# it under the terms of the GNU General Public License as published by
# the Free Software Foundation; either version 3 of the License, or
# (at your option) any later version.
#
# This program is distributed in the hope that it will be useful, but
# WITHOUT ANY WARRANTY; without even the implied warranty of MERCHANTABILITY
# or FITNESS FOR A PARTICULAR PURPOSE. See the GNU General Public License
# for more details.
#
# You should have received a copy of the GNU General Public License along
# with this program; if not, see <http://www.gnu.org/licenses/>
#
# Additional note on redistribution: The copyright and license notices above
# must be maintained in each individual source file that is a derivative work
# of this source file; otherwise redistribution is prohibited.

include $(MAKE_INC_DIR)/firmware-defs.mk

# Set developer code and compile options
# Set to YES for debugging
DEBUG ?= NO

# List of modules to include
MODULES = Sensors
MODULES += Attitude
MODULES += Actuator
MODULES += ManualControl
MODULES += Stabilization
MODULES += FirmwareIAP
MODULES += Telemetry

OPTMODULES += GPS
OPTMODULES += PathPlanner
OPTMODULES += AltitudeHold
OPTMODULES += VtolPathFollower
OPTMODULES += FixedWingPathFollower
OPTMODULES += FlightStats
OPTMODULES += CameraStab
OPTMODULES += Autotune
OPTMODULES += TxPID
OPTMODULES += VibrationAnalysis
OPTMODULES += UAVOMavlinkBridge
OPTMODULES += Battery
OPTMODULES += ComUsbBridge
OPTMODULES += Airspeed
OPTMODULES += UAVOHoTTBridge
OPTMODULES += UAVOFrSKYSensorHubBridge
OPTMODULES += UAVOFrSKYSPortBridge
OPTMODULES += UAVOLighttelemetryBridge
OPTMODULES += Geofence
OPTMODULES += Logging
OPTMODULES += VTXConfig
OPTMODULES += OnScreenDisplay
OPTMODULES += Storm32Bgc
OPTMODULES += UAVOCrossfireTelemetry
OPTMODULES += UAVOMSPBridge

# Paths
OPUAVOBJINC = $(OPUAVOBJ)/inc
PIOSINC = $(PIOS)/inc
FLIGHTLIBINC = $(FLIGHTLIB)/inc
MATHLIB = $(FLIGHTLIB)/math
MATHLIBINC = $(FLIGHTLIB)/math
MGRSLIB = $(FLIGHTLIB)/mgrs
MGRSLIBINC = $(FLIGHTLIB)/mgrs
RSCODE = $(FLIGHTLIB)/rscode
RSCODEINC = $(FLIGHTLIB)/rscode
PIOSSTM32F4XX = $(PIOS)/STM32F4xx
PIOSCOMMON = $(PIOS)/Common
PIOSCOMMONLIB = $(PIOSCOMMON)/Libraries
APPLIBDIR = $(PIOSSTM32F4XX)/Libraries
STMLIBDIR = $(APPLIBDIR)
STMSPDDIR = $(STMLIBDIR)/STM32F4xx_StdPeriph_Driver
STMSPDSRCDIR = $(STMSPDDIR)/src
STMSPDINCDIR = $(STMSPDDIR)/inc
DEBUG_CM3_DIR = $(PIOSCOMMONLIB)/Debug
DEBUG_CM3_DIR_INC = $(DEBUG_CM3_DIR)/inc
OPUAVOBJINC = $(OPUAVOBJ)/inc
FLIGHTPLANLIB = $(OPMODULEDIR)/FlightPlan/lib
FLIGHTPLANS = $(OPMODULEDIR)/FlightPlan/flightplans
MAVLINKINC = $(FLIGHTLIB)/mavlink/v1.0/common


# optional component libraries
include $(APPLIBDIR)/ChibiOS/library.mk
#include $(PIOSCOMMONLIB)/dosfs/library.mk

# List C source files here. (C dependencies are automatically generated.)
# use file-extension c for "c-only"-files

## OPENPILOT CORE:
SRC += ${OPMODULEDIR}/System/systemmod.c
SRC += ${OPMODULEDIR}/System/rgbleds.c
SRC += chibi_main.c
SRC += pios_board.c
SRC += pios_usb_board_data.c
SRC += $(OPUAVOBJ)/uavobjectmanager.c

ifeq ($(DEBUG),YES)
SRC += $(DEBUG_CM3_DIR)/dcc_stdio.c
SRC += $(DEBUG_CM3_DIR)/cm3_fault_handlers.c
endif

SRC += taskmonitor.c

## PIOS Hardware (STM32F4xx)
include $(PIOS)/STM32F4xx/library_chibios.mk
# SRC += $(PIOS)/STM32F4xx/pios_video.c

## PIOS Hardware (Common)
SRC += pios_delay.c
SRC += pios_exti.c
SRC += pios_gcsrcvr.c
SRC += pios_mpu.c
SRC += pios_hmc5883.c
SRC += pios_hmc5983_i2c.c
SRC += pios_ms5611.c
SRC += pios_etasv3.c
SRC += pios_mpxv5004.c
SRC += pios_mpxv7002.c
SRC += pios_crc.c
SRC += pios_com.c
SRC += pios_dsm.c
SRC += pios_rcvr.c
SRC += pios_sbus.c
SRC += pios_hsum.c
SRC += pios_sensors.c
SRC += pios_flash.c
SRC += pios_flash_jedec.c
SRC += pios_flashfs_logfs.c
SRC += pios_usb_desc_hid_cdc.c
SRC += pios_usb_desc_hid_only.c
SRC += pios_usb_util.c
SRC += pios_adc.c
SRC += pios_heap.c
SRC += pios_semaphore.c
SRC += pios_mutex.c
SRC += pios_thread.c
SRC += pios_queue.c
SRC += pios_streamfs.c
SRC += pios_hal.c
SRC += pios_servo.c
SRC += pios_modules.c
SRC += pios_srxl.c
SRC += pios_ibus.c
SRC += pios_spi.c
SRC += pios_irq.c
SRC += pios_pwm.c
SRC += pios_ppm.c
SRC += pios_debug.c
SRC += pios_wdg.c
SRC += pios_reset.c
SRC += pios_annunc.c
SRC += pios_annuncdac.c
SRC += pios_fskdac.c
SRC += pios_crossfire.c

# List C++ source files here.
# use file-extension .cpp for C++-files (not .C)
CPPSRC =

# List any extra directories to look for include files here.
#    Each directory must be seperated by a space.
EXTRAINCDIRS += $(SHAREDAPIDIR)
EXTRAINCDIRS += $(PIOS)
EXTRAINCDIRS += $(PIOSINC)
EXTRAINCDIRS += $(OPUAVOBJ)
EXTRAINCDIRS += $(OPUAVOBJINC)
EXTRAINCDIRS += $(OPUAVSYNTHDIR)
EXTRAINCDIRS += $(FLIGHTLIBINC)
EXTRAINCDIRS += $(MATHLIBINC)
EXTRAINCDIRS += $(RSCODEINC)
EXTRAINCDIRS += $(PIOSSTM32F4XX)
EXTRAINCDIRS += $(PIOSCOMMON)
EXTRAINCDIRS += $(BOARD_INFO_DIR)
EXTRAINCDIRS += $(STMSPDINCDIR)
EXTRAINCDIRS += $(CMSISDIR)
EXTRAINCDIRS += $(BOOTINC)
EXTRAINCDIRS += $(DEBUG_CM3_DIR_INC)
EXTRAINCDIRS += $(MAVLINKINC)
EXTRAINCDIRS += $(MGRSLIBINC)


EXTRAINCDIRS += ${foreach MOD, ${MODULES} ${OPTMODULES}, $(OPMODULEDIR)/${MOD}/inc} ${OPMODULEDIR}/System/inc

LIBS += $(UAVOBJLIB)
LIBS += $(FLIGHTLIBFILE)

# Path to Linker-Scripts
LINKERSCRIPTPATH = $(PIOSSTM32F4XX)

# Optimization level, can be [0, 1, 2, 3, s].
# 0 = turn off optimization. s = optimize for size.
# (Note: 3 is not always the best optimization level. See avr-libc FAQ.)

ifeq ($(DEBUG),YES)
CFLAGS += -O0
CFLAGS += -DGENERAL_COV
# CFLAGS += -finstrument-functions -ffixed-r10
else
CFLAGS += -Os -fconserve-stack
endif



# common architecture-specific flags from the device-specific library makefile
CFLAGS += $(ARCHFLAGS)
CFLAGS += -DDIAGNOSTICS
CFLAGS += -DDIAG_TASKS

# configure CMSIS DSP Library
CDEFS += -DARM_MATH_CM4
CDEFS += -DARM_MATH_MATRIX_CHECK
CDEFS += -DARM_MATH_ROUNDING
CDEFS += -D__FPU_PRESENT=1
CDEFS += -DUNALIGNED_SUPPORT_DISABLE
CFLAGS += -D$(STM32_TYPE)

# Debugging format.
DEBUGF = dwarf-2

# Place project-specific -D (define) and/or
# -U options for C here.
CDEFS += -DHSE_VALUE=$(OSCILLATOR_FREQ)
CDEFS += -DSYSCLK_FREQ=$(SYSCLK_FREQ)
CDEFS += -DUSE_STDPERIPH_DRIVER
CDEFS += -DUSE_$(BOARD)
ifeq ($(ENABLE_DEBUG_CONSOLE), YES)
CDEFS += -DPIOS_INCLUDE_DEBUG_CONSOLE
endif

ifeq ($(ENABLE_DEBUG_CONSOLE), YES)
CDEFS += -DPIOS_INCLUDE_DEBUG_CONSOLE
endif


# Declare all non-optional modules as built-in to force inclusion, strip off any appended varieties of module
get_mod_name = $(shell echo $(1) | sed "s/\/[^\/]*$///")
BUILTIN_DEFS := ${foreach MOD, ${MODULES}, -DMODULE_$(call get_mod_name, $(MOD))_BUILTIN }
CDEFS += ${BUILTIN_DEFS}

# Place project-specific -D and/or -U options for
# Assembler with preprocessor here.
#ADEFS = -DUSE_IRQ_ASM_WRAPPER
ADEFS = -D__ASSEMBLY__

# Compiler flag to set the C Standard level.
# c89   - "ANSI" C
# gnu89 - c89 plus GCC extensions
# c99   - ISO C99 standard (not yet fully implemented)
# gnu99 - c99 plus GCC extensions
CSTANDARD = -std=gnu99

#-----

# Compiler flags.

#  -g*:          generate debugging information
#  -O*:          optimization level
#  -f...:        tuning, see GCC manual and avr-libc documentation
#  -Wall...:     warning level
#  -Wa,...:      tell GCC to pass this to the assembler.
#    -adhlns...: create assembler listing
#
# Flags for C and C++ (arm-elf-gcc/arm-elf-g++)

CFLAGS += -g$(DEBUGF)
CFLAGS += -ffast-math
CFLAGS += -mcpu=$(MCU)
CFLAGS += $(CDEFS)
CFLAGS += $(patsubst %,-I%,$(EXTRAINCDIRS)) -I.
CFLAGS += -mapcs-frame
CFLAGS += -fomit-frame-pointer
CFLAGS += -ffunction-sections -fdata-sections
CFLAGS += -Wdouble-promotion

CFLAGS += -Wall
CFLAGS += -Werror
CFLAGS += -Wa,-adhlns=$(addprefix $(OUTDIR)/, $(notdir $(addsuffix .lst, $(basename $<))))
# Compiler flags to generate dependency files:
CFLAGS += -MD -MP -MF $(OUTDIR)/dep/$(@F).d

# flags only for C
#CONLYFLAGS += -Wnested-externs
CONLYFLAGS += $(CSTANDARD)

# Assembler flags.
#  -Wa,...:    tell GCC to pass this to the assembler.
#  -ahlns:     create listing
ASFLAGS  = $(ARCHFLAGS) -mthumb -I. -x assembler-with-cpp
ASFLAGS += $(ADEFS)
ASFLAGS += -Wa,-adhlns=$(addprefix $(OUTDIR)/, $(notdir $(addsuffix .lst, $(basename $<))))
ASFLAGS += $(patsubst %,-I%,$(EXTRAINCDIRS))

# Linker flags.
#  -Wl,...:     tell GCC to pass this to linker.
#    -Map:      create map file
#    --cref:    add cross reference to  map file
LDFLAGS = -nostartfiles -Wl,-Map=$(OUTDIR)/$(TARGET).map,--cref,--gc-sections
LDFLAGS += $(patsubst %,-L%,$(EXTRA_LIBDIRS))
LDFLAGS += $(patsubst %,-l%,$(EXTRA_LIBS))
LDFLAGS += -lc_nano -lgcc -lm
LDFLAGS += -Wl,--warn-common
LDFLAGS += -Wl,--fatal-warnings
LDFLAGS += -u _printf_float

#Linker scripts
LDFLAGS += -T memory.ld $(addprefix -T,$(LINKER_SCRIPTS_APP))

include $(MAKE_INC_DIR)/firmware-common.mk
