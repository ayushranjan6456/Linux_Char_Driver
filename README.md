Linux Character Driver

# 📦 Simple Procfs Kernel Module — Read/Write Interface

## 🔧 Project Description

This Linux kernel module creates a `/proc/ayush_module` file interface that allows userspace applications to **read from** and **write to** a kernel buffer. It demonstrates how to use the `procfs` filesystem to communicate between user space and kernel space using standard read/write system calls.

> 🧑‍💻 Created by **Ayush Ranjan** as a beginner-level kernel programming project, this module showcases core kernel concepts like `proc_create`, `copy_to_user`, `copy_from_user`, dynamic memory allocation, and file operations in the kernel.

---

## ✨ Features

- Creates a virtual file `/proc/ayush_module`
- Supports:
  - ✅ Writing messages from userspace to kernel space
  - ✅ Reading back all messages from kernel space
- In-kernel memory buffer with a maximum capacity of **1024 bytes**
- Ensures safe memory copy operations using kernel APIs
- Includes basic error handling and sanity checks
- Prints received messages to `dmesg` logs
- Demonstrates use of `proc_ops`, `copy_to_user`, `copy_from_user`, `kmalloc`, and `proc_remove`

---

## 📁 File Structure

### ├── ldd.c - Kernel module source file
### ├── user_app.py - Python script to test read/write functionality
### ├── Makefile - Build script for compiling the kernel module
### └── README.md - Project documentation

## ⚙️ Internal Buffer Logic
Maximum size: 1024 bytes

Appends new data at the end of the buffer

Ensures safe read/write using copy_to_user and copy_from_user

Automatically null-terminates after each write

Returns EOF properly on read to support tools like cat

## 🧠 Concepts Demonstrated

Linux procfs interaction

File operation hooks: .proc_read, .proc_write

Kernel-space memory allocation (kmalloc, kfree)

Safe data copying (copy_to_user, copy_from_user)

Handling file offsets and user inputs

Kernel logging (printk)