-- 1. Query para mostrar los productos más caros de cada marca
SELECT 
    m.title AS Manufacturer, 
    MAX(a.price) AS MaxPrice, 
    MAX(a.title) AS Categories
FROM 
    articles AS a
JOIN 
    manufacturers AS m ON a.manufacturer_id = m.id
GROUP BY 
    m.title
ORDER BY 
    MAX(a.price) DESC;

-- 2. Promedio de los precios
SELECT 
    m.title AS Manufacturer, 
    AVG(a.price) AS AVGPrice
FROM 
    articles AS a
JOIN 
    manufacturers AS m ON a.manufacturer_id = m.id
GROUP BY 
    m.title
ORDER BY 
    MAX(a.price) DESC;

-- 3. Cuántos productos existen en cada categoría
SELECT 
    c.title AS Categories, 
    COUNT(a.title) AS NumberOfProducts
FROM 
    articles AS a
JOIN 
    articles_categories AS ac ON a.id = ac.article_id
JOIN 
    categories AS c ON ac.category_id = c.id
GROUP BY 
    c.title;

-- 4. Cuántos productos existen en cada marca
SELECT 
    m.title AS Manufacturer, 
    COUNT(a.title) AS NumberOfProducts
FROM 
    articles AS a
JOIN 
    manufacturers AS m ON a.manufacturer_id = m.id
GROUP BY 
    m.title;

-- 5. Muestra los 5 productos más relevantes de cada marca
SELECT 
    m.title AS Manufacturer, 
    a.title AS Categories, 
    a.relevance AS Relevance
FROM 
    articles AS a
JOIN 
    manufacturers AS m ON a.manufacturer_id = m.id
WHERE 
    (
        SELECT COUNT(*)
        FROM articles AS a2
        WHERE a2.manufacturer_id = a.manufacturer_id AND a2.relevance >= a.relevance
    ) <= 5
ORDER BY 
    Manufacturer, a.relevance DESC;
