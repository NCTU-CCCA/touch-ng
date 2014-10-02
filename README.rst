The Next Generation touch command (?
========================================

What have been done
------------------------------

- creation of empty files

Todo
------------------------------

other features in original touch

- detection of existing files
- update access/modification time stamps

File Size
------------------------------

+-------------+----------------+-----------------------+
| OS          | Path           | Size (Bytes)          |
+=============+================+=======================+
| FreeBSD 9.2 | /usr/bin/touch | 12200                 |
+-------------+----------------+-----------------------+
| Arch Linux  | /bin/touch     | 60288                 |
+-------------+----------------+-----------------------+
|         50 bytes (our touch-ng now)                  |
+-------------+----------------+-----------------------+

Implementation
------------------------------

cp from /dev/null, then it will create a new empty file

original touch
------------------------------

Notice : original touch can change Access/Modify/Change time without any permission

``stat`` command can get time info of files

touch the existing files
+++++++++++++++++++++++++

- O : update
- X : not modify

+------------+--------+--------+--------+-----------------------+
| Command    | Access | Modify | Change | note                  |
+============+========+========+========+=======================+
| touch      | O      | O      | O      |                       |
+------------+--------+--------+--------+-----------------------+
| touch -a   | O      | X      | O      |                       |
+------------+--------+--------+--------+-----------------------+
| head -c1   | O      | X      | X      | need read permission  |
+------------+--------+--------+--------+-----------------------+
| chmod      | X      | X      | O      | chmod permission      |
+------------+--------+--------+--------+-----------------------+
| echo "" >> | X      | O      | O      | need write permission |
+------------+--------+--------+--------+-----------------------+
