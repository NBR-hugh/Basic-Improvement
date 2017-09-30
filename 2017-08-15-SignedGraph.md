# 符号图

## 尝试画 符号图



            --------- +
            {END}     ^                                                                                   +-> exit {end}
                      ^                                                                                   |
            (print)   ^                                                                                   |-> "user quiry history"   +->"help info"
                      ^                                                                                   |                          |
            (out)     ^              +->weather_dict ----------+  +->city_weather,user_quiry_dict -----+  +                          |
                      ^              |                         |  |                                    |  |                          |
            [function]^  main()   +->file_deal()               |  weather_query()                      |  quit()                     help()
                      ^   |       |  |                         |  |                                    |  |                          |
            (in)      ^   |       |  +<-filename,weather_dict  |  +<-weather_dict,city,user_quiry_dict |  +<-(user_quiry_dict)       +
                      ^   |       |     ^        ^             |     ^            ^    ^               |  |   ^                      |
                      ^   |       |     |        |             +-----+            |    |               +--|---+                      |    
                      ^   |       |     |        |                                |    |                  |                          |
            (judge)   ^   |       |     |        |                              ?city  |              ?q or quit                ?h or help  ?wrong -> +
                      ^   |       |     |        |                                ^    |                  ^                          ^          ^     |
                      ^   |       |     |        |                                |    |                  |                          |          |     |
            {BEGIN}   ^   +-----> + --> + -----> + -----------------------------> + -- + -----------------+------------------------> + -------- +     |
            --------- +                                                           ^                       ^                          ^                |
                      |                                                           |                       |                          |                |
                      |                                                           + ----- ------------- commond -------------------- +                |
                      |                                                                                   |                                           |
                      |                                                                                   +                                           |
            Waiting...|                                                                                (input)<-------------------------------------- +
            --------- +


- 这张图画了2个小时,总结一下经验教训:
    - 行数基本保持不变, 列数有函数名称及变量名称长度决定

- 因此,顺序应当如此:
    - 表头
    - 函数
    - 从头开始的变量
    - 判断



