# Table of contents

* [譯者序](README.md)
* [前言](intoduction/README.md)
  * [符號與規範](intoduction/symbol.md)
  * [本書的開發環境](intoduction/environments.md)
  * [關於作者](intoduction/author.md)
  * [結束前言之前](intoduction/column.md)
* [機械語言與組譯器](machine_code_assembler/README.md)
  * [CPU 與記憶體](machine_code_assembler/cpu_memory.md)
  * [什麼是組譯器](machine_code_assembler/assembler.md)
  * [C程式和所對應的組合語言](machine_code_assembler/c_assembly/README.md)
    * [簡單的範例](machine_code_assembler/c_assembly/kantan_na_rei.md)
    * [包含呼叫函式的範例](machine_code_assembler/c_assembly/kansuu_yobidashi.md)
  * [本章小結](machine_code_assembler/matome.md)
* [創造計算機等級的語言](calculator_level_language/README.md)
  * [第1步：創造能編譯1個整數的語言](calculator_level_language/step1.md)
  * [第2步：製作可以算加減法的編譯器](calculator_level_language/step2.md)
  * [第3步：加入標記解析器（tokenizer）](calculator_level_language/step3.md)
  * [第4步：改良錯誤訊息](calculator_level_language/step4.md)
  * [文法的記法與遞迴下降分析法](calculator_level_language/recursive_descendent_parsing/README.md)
    * [將文法結構表示為樹（tree）](calculator_level_language/recursive_descendent_parsing/tree_structure.md)
    * [以生成規則定義文法](calculator_level_language/recursive_descendent_parsing/production_rule.md)
    * [以 BNF 描述生成規則](calculator_level_language/recursive_descendent_parsing/bnf.md)
    * [簡單的生成規則](calculator_level_language/recursive_descendent_parsing/simaple_production_rule.md)
    * [以生成規則描述運算子的優先順序](calculator_level_language/recursive_descendent_parsing/production_rule_operator_order.md)
    * [包含遞迴的生成規則](calculator_level_language/recursive_descendent_parsing/recursive_production_rule.md)
    * [遞迴下降語法分析](calculator_level_language/recursive_descendent_parsing/recursive_descent_syntax_parsing.md)
  * [堆疊機](calculator_level_language/stack_machine/README.md)
    * [堆疊機的概念](calculator_level_language/stack_machine/concept.md)
    * [編譯成堆疊機指令](calculator_level_language/stack_machine/compile_to_stack_machine.md)
    * [以x86-64實作堆疊機的方法](calculator_level_language/stack_machine/x86-64_stack_machine.md)
  * [第5步：製作可進行四則運算的編譯器](calculator_level_language/step5.md)
  * [第6步：單項加與單項減](calculator_level_language/step6.md)
  * [第7步：比較運算子](calculator_level_language/step7/README.md)
    * [修改標記解析器](calculator_level_language/step7/modify_tokenizer.md)
    * [新的文法](calculator_level_language/step7/new_grammer.md)
    * [產生組合語言指令](calculator_level_language/step7/generate_assembly.md)
* [分離編譯與連結](separate_compile_linking/README.md)
  * [分離編譯](separate_compile_linking/separate_compilation/README.md)
    * [分離編譯與其必要性](separate_compile_linking/separate_compilation/to_separate_compile.md)
    * [標頭檔的必要性與其內容](separate_compile_linking/separate_compilation/header_file.md)
    * [連結錯誤](separate_compile_linking/separate_compilation/link_error.md)
    * [全域變數的宣告與定義](separate_compile_linking/separate_compilation/global_declare_define.md)
  * [第8步：分割檔案與修改 Makefile](separate_compile_linking/step8/README.md)
    * [分割檔案](separate_compile_linking/step8/split_files.md)
    * [修改 Makefile](separate_compile_linking/step8/modify_makefile.md)
* [函式與區域變數](function_local_variable/README.md)
  * [第9步：1個字的區域變數](function_local_variable/step9/README.md)
    * [堆疊上的變數空間](function_local_variable/step9/variable_area_on_stack.md)
    * [修改標記解析器](function_local_variable/step9/modify_tokenizer.md)
    * [修改分析器](function_local_variable/step9/modify_parser.md)
    * [左邊值與右邊值](function_local_variable/step9/left_value_right_value.md)
    * [從任意的記憶體位址取得其值](function_local_variable/step9/load_value_from_any_address.md)
    * [修改指令產生器](function_local_variable/step9/modify_code_generator.md)
    * [修改主函式](function_local_variable/step9/modify_main_function.md)
  * [第10步：複數文字的區域變數](function_local_variable/step10.md)
  * [第11步：return](function_local_variable/step11.md)
  * [1973年的C編譯器](function_local_variable/c_compiler_in_1973.md)

