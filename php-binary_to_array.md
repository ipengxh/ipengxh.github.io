# [PHP] 二进制转换为数组

```php
public static function binaryToArray($baseKey, $binary)
{
    $values = self::binaryToValues($binary);
    $definitions = self::get($baseKey);
    $array = [];
    foreach ($definitions as $key => $definition) {
        if (in_array($values, $definition['value'])) {
            $array[$key] = $definition;
        }
    }
    return $array;
}
```