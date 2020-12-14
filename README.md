# IS211_Assignment13

Login: admin
Password: password

The strucure of this all makes sense but for some reason when I enter /dashboard after /login in, I get this error which indicates that the SQL can not find
the STUDENTS table in the schema.sql.  I can not figure out how to get the table to be recognized.

@app.route('/dashboard', methods=['GET'])
def dashboard():
    cur = g.db.execute('select ID, FIRST_NAME, LAST_NAME from STUDENTS')
    students = [dict(ID=row[0], FIRST_NAME=row[1], LAST_NAME=row[2])
                for row in cur.fetchall()]
    cur1 = g.db.execute('select ID, SUBJECT, NUM_QUESTIONS, QUIZ_DATE from QUIZZES')
    quizzes = [dict(ID=row[0], SUBJECT=row[1], NUM_QUESTIONS=row[2],
                    QUIZ_DATE=row[3]) for row in cur1.fetchall()]
sqlite3.OperationalError: no such table: STUDENTS
