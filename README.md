# Decimal
A native, big/arbitrary precision Decimal class in pure Nim built off the back of the Nim BigInts package: https://github.com/def-/nim-bigints

The design is inspired by the CPython implementation of Decimal and the IBM Decimal Arithmetic Specification (http://speleotrove.com/decimal/decarith.html).

# Progress:

- [x] Settle on object design and enums
- [x] MVP object initialisation procs for various inputs (string, int, bigint, float)
- [x] Basic arithmetic (plus, minus, divide, multiply)
- [x] Number to Decimal String 
- [x] Number to Scientific String
- [ ] Number to Engineering String
- [x] Boolean operators
- [ ] Create the remainder of required procedures shown in http://speleotrove.com/decimal/daops.html
- [ ] Add all major rounding rules
- [ ] Add context object for precision and rounding
- [ ] Ensure a reasonable level of error handling
- [ ] Create extensive test suite
- [ ] Ensure that this package complies with the Decimal Arithmetic Specification, version 1.70 


# Basic arithmetic operations:

```nim
var
  x = initDecimal("112777777777777777777777777444444111111111111111111111111111111111444444444444444444444444777779999999999999999999999999999999999999999999999999999999999999999999999999999999999999999999999999999999999999999934.0")
  y = initDecimal("1244444444444442222222222222222222222444444444444422.0")
  z = initDecimal("999999999999.121212")
  a = initDecimal("10121212.121212112121212214678990")
  b = initDecimal("-1000.000000000000000121271727234552727474654252562")

echo x / y 

# 9.0625000000000161830357142589E157
    
echo y / z    

# 1.2444444444455358250666676257E39
    
echo x * z

# 112777777777678670019999999666666333333626262959596000000000000000333333333333040404000000333335555555262624269359999999999999999999999999999999999999999999999999999999999999999999999999999999999999999999999934000000000058.0000080
    
echo a + b

# 10120212.121212112121212093407262765447272525345747438
    
echo a - b

# 10122212.121212112121212335950717234552727474654252562
```
    
# Exponential calculations

```nim
var
  a = initDecimal("-5.975543")
  b = initDecimal("1224.49948")
  
echo a ^ -5

# 0.000131254173126662886

echo pow(b, 93)

# 151408503845557692688161455451835447108431379310562098924905184946047495232330089520869458443924236560548387123650341098442981720802261916208953596118006180370925303743522295828040225912366152816909107734776067977664083437385502081437181220051456046474924292361686836920559344917448828075.222712034619105279651818260964290535195597667892958201436724766360511193555130344656098400628427608663827569617598350983466539576093349652128965891746764519526204773501798720547231828263232570323258336204178874031658184989115618939692323356264842333898299722548210927256162834874844807455759293580889759180946862143069572501479860330923104848828654110783949637763229615789299900456895449295821520704805116588168677694568238366578731331197022318771246362395890679808

```
