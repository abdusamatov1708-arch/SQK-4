# SQK-4
CREATE TABLE IF NOT EXISTS oquvchilar;
    id SERIAL PRIMARY KEY,
    ism VARCHAR(50) NOT NULL,
    familya VARCHAR(50) NOT NULL,
    yosh INT,
    sinf INT,
    fan INT,
    chsb ERIC(5,1)
INSERT INTO talabalar (ism, familiya, yosh, fan, sinf, ball) VALUES
('Gulbotir', 'Aliyev', 16, 11, 'Jismoniy', 85.0),
('Gulchapchap', 'Karimova', 15, 10, 'Texnologiya', 92.5),
('Jasur', 'Rizamatov', 17, 11, 'Jismoniy', 78.0),
('OgIloy', 'Sirojiddinova', 16, 11 , 'Fizika', 95.0),
('Toshshermat', 'Hikmatov', NULL, 10 , 'Matematika', 65.5), -- Yoshi yo'q (NULL)
('Olim', 'Tursunov', 17, 11, 'Matematika', 88.0),
('Malikachapchap', 'Abduvaliyeva', 15, 10,'Ona tili',  NULL),       -- Balli yo'q (NULL)
('Temirmas', 'Xasanov', 16, 11, 'Fizika', 81.5),
('Madina', 'Eshonqulova', 16, 11, 'Fizika', 90.0),
('Farruh', 'Qodirov', 17, 11, 'Fizika', 69.0),
('Kamola', 'Asilova', 16, 11, 'Fizika', 99.0),
('Asilbek', 'Nasimov', 17, 11, 'Fizika', 94.0);


SELECT ism || ' ' || familiya AS a_lochi_talaba, ball
FROM talabalar
WHERE ball IS NOT NULL
ORDER BY ball DESC
LIMIT 3;

SELECT id, ism, familiya, yo'nalish, ball, yosh
FROM talabalar
WHERE ball > 80 AND yo'nalish = 'Dasturlash'
ORDER BY yosh ASC;

SELECT DISTINCT sinf
FROM talabalar
WHERE sinf IS NOT NULL
ORDER BY sinf ASC;


SELECT id, ism, familiya, yosh, ball
FROM talabalar
WHERE yosh IS NULL OR ball IS NULL;


(
    SELECT ism, familiya, yosh, 'Eng yosh talaba' AS status
    FROM talabalar
    WHERE yosh IS NOT NULL
    ORDER BY yosh ASC
    LIMIT 1
)
UNION ALL
(
    SELECT ism, familiya, yosh, 'Eng katta yoshli talaba' AS status
    FROM talabalar
    WHERE yosh IS NOT NULL
    ORDER BY yosh DESC
    LIMIT 1
);

SELECT id, ism, familiya, ball
FROM talabalar
ORDER BY id ASC
LIMIT 4 OFFSET 4;

SELECT sinf, ism, familiya, ball
FROM talabalar
WHERE sinf = 11 AND ball IS NOT NULL
ORDER BY ball DESC
LIMIT 5;
