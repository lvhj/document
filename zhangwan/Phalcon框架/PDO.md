```plain
 'conditions' => "package_id = :packageId: and language_id = :languageId: and playlet_id IN ({idArray:array}) and status = 1 and is_deleted = 0",
            'bind' => ['packageId' => $defaultPackageId, 'idArray' => $playletId, "languageId" => $languageId],
```

```plain
$redis = DiUtils::redis();

$redis->hmset("a1", [
    "name" => 'name-a1',
    "sort" => 1,
]);
$redis->hmset("a2", [
    "name" => 'name-a2',
    "sort" => 2,
]);
$pipeline = $redis->pipeline();
$pipeline->hgetall("a1");
$pipeline->hgetall("a3");
$pipeline->hgetall("a2");

// 执行所有命令并获取结果
$data = $pipeline->exec();
echo json_encode($data, 320);
die;
echo json_encode($a1);
echo json_encode($a2);
echo json_encode($a3);
die;
```