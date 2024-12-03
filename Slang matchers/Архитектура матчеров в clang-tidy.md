Сорцы MatchASTVisitor лежат в https://github.com/llvm/llvm-project/blob/31bde711c4098b3136edd1cb92dd4e0cc1d4d179/clang/lib/ASTMatchers/ASTMatchFinder.cpp#L421. 
Вся архитектура строится на основа CRTP.
Из-за наследования от RecursiveASTVisitor схема обхода узла выглядит след образом https://github.com/llvm/llvm-project/blob/31bde711c4098b3136edd1cb92dd4e0cc1d4d179/clang/include/clang/AST/RecursiveASTVisitor.h#L89 ([альтернатива RecursiveASTVisitor из slang](https://github.com/jirol9xa/slang/blob/4103f38793c7c5fe99bc7678b9a26eef852a30ec/include/slang/ast/ASTVisitor.h#L57) )

**В какой момент времени clang-tidy решает, что поддерево совпало и куда он сохраняет нужные поддеревья???** 
--

в этой [функции](https://github.com/llvm/llvm-project/blob/e8b9e1354accf33ced45321abdd8c8bc65d025cc/clang/include/clang/ASTMatchers/ASTMatchFinder.h#L201) происходит поиск всех поддеревьев
[MatchASTVisitor](https://github.com/llvm/llvm-project/blob/e8b9e1354accf33ced45321abdd8c8bc65d025cc/clang/lib/ASTMatchers/ASTMatchFinder.cpp#L421) обходит дерево

	Кто стоит над ним?

MatchFinder создает кучу MatchASTVisitor'ов в [этой функции](https://github.com/llvm/llvm-project/blob/e8b9e1354accf33ced45321abdd8c8bc65d025cc/clang/lib/ASTMatchers/ASTMatchFinder.cpp#L1695) 
Обход всего дерева начинается [отсюда](https://github.com/llvm/llvm-project/blob/e8b9e1354accf33ced45321abdd8c8bc65d025cc/clang/lib/ASTMatchers/ASTMatchFinder.cpp#L1445) 
Сравнение происходит в подобных [местах](https://github.com/llvm/llvm-project/blob/e8b9e1354accf33ced45321abdd8c8bc65d025cc/clang/lib/ASTMatchers/ASTMatchFinder.cpp#L1065) 


