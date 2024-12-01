Сорцы MatchASTVisitor лежат в https://github.com/llvm/llvm-project/blob/31bde711c4098b3136edd1cb92dd4e0cc1d4d179/clang/lib/ASTMatchers/ASTMatchFinder.cpp#L421. 
Вся архитектура строится на основа CRTP.
Из-за наследования от RecursiveASTVisitor схема обхода узла выглядит след образом https://github.com/llvm/llvm-project/blob/31bde711c4098b3136edd1cb92dd4e0cc1d4d179/clang/include/clang/AST/RecursiveASTVisitor.h#L89 ([альтернатива RecursiveASTVisitor из slang](https://github.com/jirol9xa/slang/blob/4103f38793c7c5fe99bc7678b9a26eef852a30ec/include/slang/ast/ASTVisitor.h#L57) )


