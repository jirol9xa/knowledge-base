### 1. How are the UEFI bootloader parameters transmitted to the kernel, and where are they stored?

Loader_block pointer -> r12 (in kern/bootstrap.S)->uefi_lp (in kern/entry.S)
uefi_lp is a global pointer that points to the arguments from bootloader to the kernel.

### 2. Which stack does kernel C-code use and where does It allocate?
Stack is allocated in kern/entry.S. Stack is allocated in .data section and has size 16 * PAGE_SIZE (PAGE_SIZE = 1 << PAGE_SHIFT (PAGE_SHIFT = 12)).

### 3. At what point does the code start executing at the "upper" addresses?

After setting up the page table.

### 4. What values of CR3 and GDT are used during kernel execution?
CR3 has the value 0x2001000.  ??????
Need to ask about leaq pml4(%rip), %rax. Because result is always the same, but rip whould change on every command. It is very strange. Also need to know how print value of pml4 in gdb (p (int) pml4 works strange).

### 5. Why is there no need to update the GDT in the start code, unlike CR3?
Because CR3 is used for memory address translating, but the memory itself is not a virtual and has only one segment, so no need to save info about it in GDT. 


