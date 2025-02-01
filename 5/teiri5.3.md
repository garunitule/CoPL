|- let rec f = fun x -> f x in f 2 evalto v by E-LetRec{
    f = ()[rec f = fun x -> f x] |- f 2 evalto v by E-AppRec{
        f = ()[rec f = fun x -> f x] |- f evalto ()[rec f = fun x -> f x] by E-Var1{};
        f = ()[rec f = fun x -> f x] |- 2 evalto 2 by E-Int{};
        f = ()[rec f = fun x -> f x], x = 2 |- f x evalto v by E-AppRec{
            f = ()[rec f = fun x -> f x], x = 2 |- f evalto ()[rec f = fun x -> f x] by E-Var2{
                f = ()[rec f = fun x -> f x] |- f evalto ()[rec f = fun x -> f x] by E-Var1{};
            }; 
            f = ()[rec f = fun x -> f x], x = 2 |- x evalto 2 by E-Var1{};
            // 下記が再帰的に登場する。そのため評価が終了しないプログラムとなっている
            f = ()[rec f = fun x -> f x], x = 2 |- f x evalto by E-AppRec{

            };
        };
    };
};