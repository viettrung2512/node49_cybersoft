# node49_cybersoft


-- Tìm 5 người đã like nhà hàng nhiều nhất.
SELECT user_id, COUNT(*) AS like_count
FROM like_res
GROUP BY user_id
ORDER BY like_count DESC
LIMIT 5;

-- Tìm 2 nhà hàng có lượt like nhiều nhất.
SELECT res_id, COUNT(*) AS like_count
FROM like_res
GROUP BY res_id
ORDER BY like_count DESC
LIMIT 2;

--Tìm người đã đặt hàng nhiều nhất
SELECT user_id, COUNT(*) AS order_count
FROM orders
GROUP BY user_id
ORDER BY order_count DESC
LIMIT 1;

--Tìm người dùng không hoạt động trong hệ thống 
SELECT users.user_id, users.full_name, users.email
FROM users
LEFT JOIN orders ON users.user_id = orders.user_id
LEFT JOIN like_res ON users.user_id = like_res.user_id
LEFT JOIN rate_res ON users.user_id = rate_res.user_id
WHERE orders.user_id IS NULL AND like_res.user_id IS NULL AND rate_res.user_id IS NULL;
