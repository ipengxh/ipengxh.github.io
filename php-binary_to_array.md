# [PHP] 二进制转换为数组

如果你有更好的方法, 请提交一个 PR

```php
public static function binaryToValues($binary)
{
    $values = [];
    $byte = 0;
    while ($binary) {
        if($binary & 1) { // 判断当前值的二进制最后一位是否为1
            $values[] = pow(2, $byte);
        }
        $binary = $binary >> 1;
        $byte++;
    }
    return $values;
}
```
