# mrubyc-gem-vl53l0x
mruby/c sources for VL53L0X

## device
https://www.switch-science.com/catalog/3647/

## sample code

```ruby
i2c = I2C.new(22, 21)
vl53l0x = VL53L0X.new(i2c)
vl53l0x.set_timeout(500) # タイムアウト

if !vl53l0x.init
  puts "Failed to detect and initialize sensor!"
else
  vl53l0x.start_continuous(100) # 100 ms 間隔で計測. タイムアウトより小さい値にしておく．
  loop do
    puts vl53l0x.read_range_continuous_millimeters
    puts " TIMEOUT" if vl53l0x.timeout_occurred
  end
end
```
