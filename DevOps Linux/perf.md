## CLI Usage

    perf top             # Shows incomplete details!!!
    perf top -a          # Shows usage per symbol on all CPUs
    perf top -a -g       # Shows usage with call-graphs on everything
    
    perf top -a -ns comm,dso    # Show usage per process+symbol tuples
