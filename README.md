# uv3dp
Tools for UV Resin based 3D Printers (in Go)

## Supported File Formats

This tool is for devices that use the Prusa SL1 (`*.sla`) and ChiTuBox DLP (`*.cbddlp`) format files.

Printers known to work with this tool:

| Printer      | File Formats | Issues                                            |
| ------------ | ------------ | --------------------------------------------------|
| EPAX X-1     | cbddlp       | None                                              |

## Installation

* Release package: [https://github.com/ezrec/uv3dp/releases](https://github.com/ezrec/uv3dp/releases)
* Go install: `go get github.com/ezrec/uv3dp/cmd/uv3dp; ${GOROOT}/bin/uv3dp`

## Command Line Tool (`uv3dp`)

The command line tool is designed to be used in a 'pipeline' style, for example:

    uv3dp foo.sl1 info                    # Shows information about the SL1 file
    uv3dp foo.sl1 decimate bar.cbddlp     # Convert and decimates a SL1 file to a CBDDLP file
    uv3dp foo.sl1 qux.cbddlp --version 1  # Convert a SL1 file to a Version 1CBDDLP file

### Command summary:

    Usage:
    
      uv3dp [options] INFILE [command [options] | OUTFILE]...
    
    Options:
    
      -v, --verbose count   Verbosity
    
    Commands:
    
      (none)               Translates input file to output file
      info                 Dumps information about the printable
      decimate             Remove outmost pixels of all islands in each layer (reduces over-curing on edges)
      exposure             Alters exposure times
    
    Options for 'info':
    
      -e, --exposure   Show summary of the exposure settings (default true)
      -l, --layers     Show summary of the layers (default true)
    
    Options for 'decimate':
    
    
    Options for 'exposure':
    
          --bottom-count uint          Bottom layer count
          --bottom-exposure duration   Bottom layer light-on time
          --exposure duration          Normal layer light-on time
    
    Options for '*.cbddlp':
    
          --version uint32   Override header Version (default 2)
    
    Options for '*.photon':
    
          --version uint32   Override header Version (default 1)
    
    Options for '*.sl1':
    
      -m, --material-name string   config.init entry 'materialName' (default "3DM-ABS @")
