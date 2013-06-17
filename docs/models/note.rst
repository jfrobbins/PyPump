
Note
====

This object represents pump.io's notes, these are used to post text to a `person`'s inbox. 

.. py:class:: Note

    This represents a note, short-form text message, these appear in the stream
    

    .. py:attribute:: content

        This is the content of the Note

	    >>> my_note = Note("I'm posting on pump.io")
            >>> my_note.content
            "I'm posting on pump.io" 

    .. py:attribute:: actor

        This is who posted the Note (Person object)

            >>> my_note = Note("I'm posting on pump.io")
            >>> my_note.actor
            <Person: Tsyesika@pump.megworld.co.uk>

    .. py:attribute:: updated

        This is when it was last updated (posted, commented, etc.) this is a datetime.datetime object

            >>> my_note.updated
	    datetime.datetime(2013, 6, 15, 12, 31, 22, 134180)

    .. py:attribute:: published

        This is when the Note was first published, this is a datetime.datetime object

	    >>> my_note.published
            datetime.datetime(2013, 6, 15, 12, 31, 22, 134180)

    .. py:attribute:: to

        This is a list of person objects, who the Note was to

            >>> my_note.to
            [<Person: Tsyesika@pump.megworld.co.uk>, <Person: Tuteo@another.server.co.uk>]

    .. py:attribute:: cc

        This is a list of person objects, who was carbon copied into the Note

            >>> my_note.cc
            [<Person: someone@microca.st>]         

    .. py:method:: comment(comment)

        This takes in a Comment object, this will send
	the comment to the remote server.

    .. py:method:: delete()

        This will delete the object.


Example
-------

This shows making a new post

    >>> from models.note import Note
    >>> my_note = Note("This is a new note!")

You want to comment?



    >>> from models.comment import Comment
    >>> my_comment = Comment("I'm commenting on my note")
    >>> my_note.comment(my_comment)


You can like the note

    >>> my_comment.like()

Oh wait? you didn't want to...

    >>> my_comment.unlike()

Oh you didn't want to post the note?

    >>> my_comment.delete()
    >>> my_comment = None # we don't want to accidently try and use a deleted comment

.. warning:: Using a comment object after deletion will raise a DoesNotExist exception
