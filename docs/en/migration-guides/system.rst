Migrate System to ESP-IDF 5.0
==================================

Inter-Processor Call
-----------------------

IPC (Inter-Processor Call) component has been moved to ``esp_system``.

Thus, any project presenting a ``CMakeLists.txt`` file with the parameters ``PRIV_REQUIRES esp_ipc`` or ``REQUIRES esp_ipc``, should be modified to simply remove these options as ``esp_system`` component is included by default.

ESP Clock
---------

The old headers ``{IDF_TARGET_NAME}/clk.h``, ``esp_clk.h`` have been removed.

Therefore, If you want to use the function with the prefix ``esp_clk`` please include ``esp_private/esp_clk.h`` instead.

Cache Error Interrupt
---------------------

The old headers ``{IDF_TARGET_NAME}/cache_err_int.h`` have been removed. Please include ``esp_private/cache_err_int.h`` instead.

Brownout
--------

The header ``brownout.h`` has been made private. ESP-IDF developers should include ``esp_private/brownout.h`` instead.

Trax
----

The header ``trax.h`` has been made private. ESP-IDF developers should include ``esp_private/trax.h`` instead.

ROM
---
Deprecated ROM related header files from `components/esp32/rom/` (old include path: `rom/*.h`) have been deleted. Please update to use the new target-specific path from `components/esp_rom/include/{IDF_TARGET_NAME}/` (new include path: `{IDF_TARGET_NAME}/rom/*.h`).

Tasks snapshot
--------------

The header ``task_snapshot.h`` has been removed from ``freertos/task.h``. ESP-IDF developers should include ``"freertos/task_snapshot.h``` in case they need tasks snapshot API.

ESP HW Support
--------------

- The header files ``soc/cpu.h`` have been deleted and deprecated CPU util functions have been removed. ESP-IDF developers should include ``esp_cpu.h`` instead for equivalent functions.
- The header file ``esp_intr.h`` has been deleted. Please include ``esp_intr_alloc.h`` to allocate and manipulate interrupts.
- The header file ``esp_panic.h`` has been deleted. ESP-IDF developers should include ``esp_private/panic_reason.h`` to get supported panic reasons. And should include ``esp_debug_helpers.h`` to use any debug related helper functions, e.g. print backtrace.
