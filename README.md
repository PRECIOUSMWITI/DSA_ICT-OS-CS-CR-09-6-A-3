CLASS SongNode:
BEGIN
    DATA title
    DATA artist
    POINTER next = NULL

CLASS Playlist:
    POINTER head = NULL

    METHOD addSong(title, artist):
        CREATE newSong from SongNode(title, artist)
        
        IF head is NULL:
            SET head = newSong
        ELSE:
            SET current = head
            WHILE current.next is NOT NULL:
                current = current.next  // Move to the last song
            END WHILE
            SET current.next = newSong   // Link new song at the end
        END IF
        PRINT "Added " + title

    METHOD displayAll():
        IF head is NULL:
            PRINT "The playlist is empty."
            RETURN
            
        SET current = head
        PRINT "--- Current Playlist ---"
        WHILE current is NOT NULL:
            PRINT current.title + " by " + current.artist
            SET current = current.next  // Move to the next song
        END WHILE

// MAIN EXECUTION
BEGIN
    CREATE myPlaylist
    
    CALL myPlaylist.addSong("Bohemian Rhapsody", "Queen")
    CALL myPlaylist.addSong("Blinding Lights", "The Weeknd")
    CALL myPlaylist.addSong("Stay", "The Kid LAROI")
    
    CALL myPlaylist.displayAll()
END
