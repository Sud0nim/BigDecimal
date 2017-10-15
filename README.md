# BigDecimal
An attempt to build a native BigDecimal class in Nim off the back of the Nim BigInts package: https://github.com/def-/nim-bigints

This is highly experimental and I have no experience in actually building a decimal class. Please use at your own risk, but feel free to contribute.

# Some preliminary tests of arithmetic with arbitrary precision decimal types:

Input:

    var
      x = newDecimal("112777777777777777777777777444444111111111111111111111111111111111444444444444444444444444777779999999999999999999999999999999999999999999999999999999999999999999999999999999999999999999999999999999999999999934.0")
      y = newDecimal("1244444444444442222222222222222222222444444444444422.0")
      z = newDecimal("999999999999.121212")
      a = newDecimal("10121212.121212112121212214678990")
      b = newDecimal("-1000.000000000000000121271727234552727474654252562")
  
    echo x / y
    echo y / z
    echo x * z
    echo a + b
    echo a - b
    
Output:

    # echo x / y :  
    90625000000000161830357142589574429193000159954339450231471857289780848499459693727052506943148357414243207436017985101914339047458766791490808059955137208949.5175572158242949872423988810273634086654860564131064180173149113983086154947520875673792399277247296682697161711778257678477574663173668058102941428904870672191000712421175015525922022021277318591703373623196820103530133682766399077474571973209235121950989515788442317129025949557
    
    # echo y / z :      
    1244444444445535825066667625758860909153.9498223050555812564438151841411877474580410660982131569923943165438070322166468991
    
    # echo x * z :
    112777777777678670019999999666666333333626262959596000000000000000333333333333040404000000333335555555262624269359999999999999999999999999999999999999999999999999999999999999999999999999999999999999999999999934000000000058.000008000000000
    
    # echo a + b :
    10120212.121212112121212093407262765447272525345747438
    
    # echo a - b:
    10122212.121212112121212335950717234552727474654252562
    
    
    
# First experiments with exponential calculations

Input:

    var
      a = newDecimal("-5.975543")
      b = newDecimal("1224.49948")
    echo "-5.975543 ^ -5 = ", a ^ -5
    echo "1224.49948 ^ 93 = ", pow(b, 93)

Output:

    -5.975543 ^ -5 = 0.000131254173126662886
    1224.49948 ^ 93 = 151408503845557692688161455451835447108431379310562098924905184946047495232330089520869458443924236560548387123650341098442981720802261916208953596118006180370925303743522295828040225912366152816909107734776067977664083437385502081437181220051456046474924292361686836920559344917448828075.222712034619105279651818260964290535195597667892958201436724766360511193555130344656098400628427608663827569617598350983466539576093349652128965891746764519526204773501798720547231828263232570323258336204178874031658184989115618939692323356264842333898299722548210927256162834874844807455759293580889759180946862143069572501479860330923104848828654110783949637763229615789299900456895449295821520704805116588168677694568238366578731331197022318771246362395890679808
288
