LPC21ISP_Win
============

LPC21ISP Pre-compiled for Windows

I removed an if-statement that was preventing from the FTDI automatic reset from working fully.  It'd put the LPC1114 into program mode, but after the program was uploaded the function that reset it back into run mode would never execute.  I simply commented the if statement out.  I'm sure I've cost some robustness, but hey, it works. :)

    //THOMAS BRITTAIN: Not sure what this if statement is doing, but it keeps it from entering RUN_MODE after upload.
    //if (IspEnvironment->StartAddress == 0 || IspEnvironment->TerminalOnly)
	  //{
        /* Only reset target if startaddress = 0
        * Otherwise stay with the running program as started in Download()
        */
        ResetTarget(IspEnvironment, RUN_MODE);
    //}
    
I believe StartAddress never equals "0"?
