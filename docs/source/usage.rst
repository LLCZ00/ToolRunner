Basic Usage
===========
The basic function of *toolrunner* is running commands defined either though *toolrunner.Tools* methods, 
or a python dictionary.

Running Tools & Commands
------------------------
>>> import toolrunner
>>> elftools = toolrunner.Tools("/home/User/Desktop/susElf", "tool_output") # CWD/tool_output
>>> elftools.cli("capa details", "/home/User/Downloads/capa-v4.0.1-linux/capa", ["-vv"])
>>> elftools.cli("elf info ", "readelf", ['-a'])
>>> elftools.gui("IDA Pro", "/home/User/idafree-7.7/ida64")
>>> elftools.run_all()

Results:

- IDA Pro is opened, loaded with our input file
- susElf's capability details and ELF info are written to *./tool_output/capa_details.txt* and *./tool_output/elf_info.txt*, respectively

Tool Configuration Dictionary
-----------------------------
Continuing with the previous example, the *print_config()* method can be called to print the configuration of the Tools instance:

>>> elftools.print_config()
toolrunner_config = {
	"cli" : {
		"capa details" : ['/home/User/Downloads/capa-v4.0.1-linux/capa', '-vv'],
		"elf info" : ['readelf', '-a'],
	},
	"gui" : {
		"IDA Pro" : ['/home/User/idafree-7.7/ida64'],
	},
}

This dictionary can be copied, edited, and used as the tool configuration in other scripts/*Tools* instances. 

.. code-block:: python
        
    """
    Automating some static analysis procedures - ELF
    """
    import toolrunner

    static_elf = {
    	"cli" : {
    		"capa details" : ['/home/User/Downloads/capa-v4.0.1-linux/capa', '-vv'],
    		"elf info" : ['readelf', '-a'],
    	},
    	"gui" : {
    		"IDA Pro" : ['/home/User/idafree-7.7/ida64'],
    	},
    }

    target = toolrunner.get_argv() # Accept file path from argv (via drag/drop or command-line)
    elftools = toolrunner.Tools(target, "static_reports", config=static_elf)

    elftools.run_all()
    toolrunner.run(["file", f"{target}"]) # Run individual command (file)

Results:

IDA is started, the files are created/written in the same manner as before, and the output from the *file* command is written to the console.

.. code-block:: console

    /home/User/Desktop/susElf: ELF 64-bit LSB executable, x86-64, version 1 (SYSV), dynamically linked, 
    interpreter /lib64/ld-linux-x86-64.so.2, BuildID[sha1]=4718ca7956738ceeb119adf941242af1824df77c, 
    for GNU/Linux 3.2.0, not stripped
