# oson-css325

This is a music player webapp, for CSS 325.

- For user Data --main-font:'Kanit';
<!DOCTYPE html>
<!--Font-->
<link rel="preconnect" href="https://fonts.googleapis.com/%22%3E">
<link rel="preconnect" href="https://fonts.gstatic.com/" crossorigin>
<link href="https://fonts.googleapis.com/css2?family=Kanit:wght@300;400;500;700&display=swap" rel="stylesheet">

- For website headers and texts --main-font:'Typo Round Regular Demo';

INSERT INTO `artist`(`ArtistEmail`, `ArtistPassword`, `ArtistName`, `ArtistGenre`, `AmountOfFollowers`, `Banking_Information`, `Country`, `ArtistRealNames`, `profile_url`) VALUES ('palewaves@gmail.com','palewaves','Pale Waves','Indie','6000','KGB-0123456789','England', 'Heather Baron-Gracie','img/1')

INSERT INTO `listener` (`UserEmail`, `UserPassword`, `Gender`, `UserName`, `UserDateOfBirth`, `PreferredGenre`, `CreationTimeStamp`, `Country`, `profile_url`) VALUES ('leon@gmail.com', 'leon', 'Male', 'leonardo', '26-Jun-2000', 'Indie', 'current_timestamp(2)', 'Germany', 'img/1') 

INSERT INTO `song` (`Duration`, `Genre`, `Name`, `Language`, `Popularity`, `Explicity`, `ReleaseDate`, `song_url`, `cover_url`) VALUES ('2.36', 'Rap', 'God\'s plan', '0', 'English', 'E', '2018-01-19', 'song/1', 'cover/1');

INSERT INTO `createsong` (`idArtist`, `idSong`, `EntryOfArtist`) VALUES ('2', '1', '1');

INSERT INTO `listentosong` ( `idListener`, `idSong`, `DurationListenedTo`) VALUES ('1', '1', '1.36') '

SELECT `song`.*, COUNT(`ListenToSongId`)FROM `artist`, `song`, `createsong`, `ListenToSong` WHERE `artist`.`idArtist` = 2 AND `artist`.`idArtist` = `createsong`.`idArtist` AND `createsong`.`idSong` = `song`.`idSong` AND `ListenToSong`.`idSong` = `song`.`idSong` ORDER BY COUNT(`ListenToSongId`) LIMIT 0,3 ; 

SELECT DISTINCT `song`.* , COUNT(`ListenToSongId`) FROM `artist`, `song`, `createsong`, `ListenToSong` WHERE `artist`.`idArtist` = 2 AND `artist`.`idArtist` = `createsong`.`idArtist` AND `createsong`.`idSong` = `song`.`idSong` AND `ListenToSong`.`idSong` = `song`.`idSong` LIMIT 0,3; 

SELECT DISTINCT `song`.* , COUNT(`ListenToSongId`) FROM `artist`, `song`, `createsong`, `ListenToSong` WHERE `artist`.`idArtist` = 2 AND `artist`.`idArtist` = `createsong`.`idArtist` AND `createsong`.`idSong` = `song`.`idSong` AND `ListenToSong`.`idSong` = `song`.`idSong` GROUP BY `idSong` ORDER BY COUNT(`ListenToSongId`) DESC LIMIT 0,3; 

Total new streams
SELECT count(DISTINCT `ListenToSongid`)
FROM `listener`, `song`, `createsong`, `ListenToSong`, `artist` 
WHERE `ListenToSong`.`idSong` = `song`.`idSong`
AND `song`.`idSong`  = `createsong`.`idSong`
AND `createsong`.`idArtist` = `artist`.`idArtist`
AND `artist`.`idArtist` = 2;

Total new listener
SELECT count(DISTINCT `ListenToSong`.`idListener`)
FROM `listener`, `song`, `createsong`, `ListenToSong`, `artist` 
WHERE `ListenToSong`.`idSong` = `song`.`idSong`
AND `song`.`idSong`  = `createsong`.`idSong`
AND `createsong`.`idArtist` = `artist`.`idArtist`
AND `artist`.`idArtist` = 2;

New follows
SELECT count(DISTINCT `FollowArist`.`idListener`)
            FROM `listener`, `song`, `createsong`, `FollowArist`, `artist` 
            WHERE `FollowArist`.`idArtist` = `artist`.`idArtist`
            AND YEARWEEK(`FollowDate`, 1) = YEARWEEK(CURDATE(), 1);

New Donation Sum
SELECT SUM(`donatetoartist`.`amount`)
            FROM `donatetoartist`, `artist` 
            WHERE `donatetoartist`.`idArtist` = `artist`.`idArtist`
            AND `artist`.`idArtist` = 2
            AND YEARWEEK(`DonateTimeStamp`, 1) = YEARWEEK(CURDATE(), 1);

SELECT album.* FROM album,artist where album.artistid = artist.artistid

SELECT song.* FROM song, album, consistsalbum WHERE album.albumid = consistsalbum.albumid AND consistsalbum.songid = song.songid;