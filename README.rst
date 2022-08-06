================================
Django Create Fake Model Object
================================

Django Create Fake Model Object is a Django app to make random fake data
It also creates Foreign objects and M2M objects!


Quick Start
============

1. Add "create_fake_model_object" to your INSTALLED_APPS setting like this::

    INSTALLED_APPS = [
        ...,
        'create_fake_model_object',
    ]


2. If you want to create a new model object use the following command to create.::

    python manage.py createrandom (appname) (Modelname) (option -n createnumber)

    # Example
    python manage.py createrandom book Book -n 7



Example
============

models.py::

    # [account app]
    # account/models.py

    class User(AbstractUser):
        nickname = models.CharField(max_length=45, blank=True, null=True, db_index=True, unique=True)

        class Meta:
            managed = True
            db_table = 'account_user'

    # [book app]
    # book/models.py

    class Book(models.Model):
        title = models.CharField(max_length=45)
        description = models.TextField()
        author = models.ForeignKey(User, models.CASCADE)

commands::

    # create 10 random users
    python manage.py createrandom account User -n 10

    mysql> select id, nickname from account_user;
    +----+------------------+
    | id | nickname         |
    +----+------------------+
    |  1 | baileyjason      |
    | 10 | daviscraig       |
    |  7 | jacksonsheila    |
    |  2 | joshualindsey    |
    |  9 | martinezjennifer |
    |  5 | ptucker          |
    |  8 | terriwilson      |
    |  4 | thamilton        |
    |  6 | walter45         |
    |  3 | whayes           |
    +----+------------------+

    # create 50 random books
    python manage.py createrandom book Book -n 50

    mysql> select * from book_book\G
    *************************** 1. row ***************************
             id: 1
          title: Part end tough wish issue lot.
    description: Never radio open every. Become for one seven. Before man out in.
    Film side media. Data treat result right practice case. Yes get film.
      author_id: 4
    *************************** 2. row ***************************
             id: 2
          title: Ok moment build across go whole citizen.
    description: Too different walk call thought hundred south. Nothing on since director. Give enter community question back while.
    Contain figure nation course. Address including fill building small.
      author_id: 9
    *************************** 3. row ***************************
             id: 3
          title: Remember return look remain recently spring d
    description: Full dream top check local campaign. Especially realize move.
    Pass recognize along travel. Everyone organization both paper friend sure provide.
      author_id: 7
    *************************** 4. row ***************************
             id: 4
          title: Claim son air.
    description: Defense young speak there media behavior protect street. True pass west light most. Poor with result human result director pressure.
      author_id: 1
    *************************** 5. row ***************************
             id: 5
          title: Author home throughout story.
    description: Sound a those each less. Director late direction eight heart radio his order. Receive company important quite major.
      author_id: 8
    *************************** 6. row ***************************
             id: 6
          title: Home pick seem idea great dark fish.
    description: Worry edge modern check public.
    Within note budget choice manager rock conference. Specific believe if or spring one people.
      author_id: 10
    *************************** 7. row ***************************
             id: 7
          title: Upon practice million present.
    description: Nature respond ever side figure foot. Quite wrong beat tax respond major.
    Suddenly late billion cover. Job environmental early. Key grow wide remain.
      author_id: 1
    *************************** 8. row ***************************
             id: 8
          title: Top let significant change participant.
    description: On prepare expect father. Suggest interesting lawyer line. Lot shoulder purpose. Receive yard voice pretty kitchen girl.
      author_id: 8
    *************************** 9. row ***************************
             id: 9
          title: Player executive question feel sing myself yo
    description: Itself garden big ahead appear hear city.
      author_id: 5
    *************************** 10. row ***************************
    ....
    has more datas!


Extra
========
ManyToManyField: If you want to create a new model objects with M2M Field! M2M Field Must be `blank=True`
