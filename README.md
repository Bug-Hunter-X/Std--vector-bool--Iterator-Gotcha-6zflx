# std::vector<bool> Iterator Problem

This repository demonstrates a common, subtle bug involving the use of `std::vector<bool>` in C++.  `std::vector<bool>` is specially implemented in most standard libraries for memory efficiency (using bit packing).  However, this optimization causes its iterators to *not* be random access iterators, unlike other `std::vector` specializations. This can lead to unexpected results when used with algorithms that rely on random access, such as `std::sort`, `std::find`, etc.

## The Bug
The bug arises from the assumption that iterators for `std::vector<bool>` behave like iterators for other `std::vector` types.  This assumption is incorrect.

## Solution
The solution involves using a different data structure (e.g., `std::vector<int>` with a bitwise representation, or a more appropriate container) or explicitly using algorithms designed to handle the non-random access nature of `std::vector<bool>` iterators. For simple operations, explicit loops often provide better control and clarity.
