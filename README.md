# library_sql
-- MySQL dump 10.13  Distrib 8.0.28, for macos11 (x86_64)
--
-- Host: 127.0.0.1    Database: library
-- ------------------------------------------------------
-- Server version	8.0.28

/*!40101 SET @OLD_CHARACTER_SET_CLIENT=@@CHARACTER_SET_CLIENT */;
/*!40101 SET @OLD_CHARACTER_SET_RESULTS=@@CHARACTER_SET_RESULTS */;
/*!40101 SET @OLD_COLLATION_CONNECTION=@@COLLATION_CONNECTION */;
/*!50503 SET NAMES utf8 */;
/*!40103 SET @OLD_TIME_ZONE=@@TIME_ZONE */;
/*!40103 SET TIME_ZONE='+00:00' */;
/*!40014 SET @OLD_UNIQUE_CHECKS=@@UNIQUE_CHECKS, UNIQUE_CHECKS=0 */;
/*!40014 SET @OLD_FOREIGN_KEY_CHECKS=@@FOREIGN_KEY_CHECKS, FOREIGN_KEY_CHECKS=0 */;
/*!40101 SET @OLD_SQL_MODE=@@SQL_MODE, SQL_MODE='NO_AUTO_VALUE_ON_ZERO' */;
/*!40111 SET @OLD_SQL_NOTES=@@SQL_NOTES, SQL_NOTES=0 */;

--
-- Table structure for table `Books`
--

DROP TABLE IF EXISTS `Books`;
/*!40101 SET @saved_cs_client     = @@character_set_client */;
/*!50503 SET character_set_client = utf8mb4 */;
CREATE TABLE `Books` (
  `BookID` int NOT NULL AUTO_INCREMENT,
  `Title` varchar(255) NOT NULL,
  `Author` varchar(255) NOT NULL,
  `Genre` varchar(100) DEFAULT NULL,
  `PublishedYear` int DEFAULT NULL,
  PRIMARY KEY (`BookID`)
) ENGINE=InnoDB AUTO_INCREMENT=7 DEFAULT CHARSET=utf8mb4 COLLATE=utf8mb4_0900_ai_ci;
/*!40101 SET character_set_client = @saved_cs_client */;

--
-- Dumping data for table `Books`
--

LOCK TABLES `Books` WRITE;
/*!40000 ALTER TABLE `Books` DISABLE KEYS */;
INSERT INTO `Books` VALUES (1,'The Great Gatsby','F. Scott Fitzgerald','Fiction',1925),(2,'To Kill a Mockingbird','Harper Lee','Fiction',1960),(3,'1984','George Orwell','Dystopian',1949),(4,'The Catcher in the Rye','J.D. Salinger','Fiction',1951),(5,'Moby-Dick','Herman Melville','Adventure',1851),(6,'Naa chavvu nenu chasta niku endhuku','Jeevan','Adventure',2025);
/*!40000 ALTER TABLE `Books` ENABLE KEYS */;
UNLOCK TABLES;

--
-- Table structure for table `BorrowedBooks`
--

DROP TABLE IF EXISTS `BorrowedBooks`;
/*!40101 SET @saved_cs_client     = @@character_set_client */;
/*!50503 SET character_set_client = utf8mb4 */;
CREATE TABLE `BorrowedBooks` (
  `BorrowID` int NOT NULL AUTO_INCREMENT,
  `MemberID` int DEFAULT NULL,
  `BookID` int DEFAULT NULL,
  `BorrowDate` date DEFAULT NULL,
  `ReturnDate` date DEFAULT NULL,
  PRIMARY KEY (`BorrowID`),
  KEY `MemberID` (`MemberID`),
  KEY `BookID` (`BookID`),
  CONSTRAINT `borrowedbooks_ibfk_1` FOREIGN KEY (`MemberID`) REFERENCES `Members` (`MemberID`),
  CONSTRAINT `borrowedbooks_ibfk_2` FOREIGN KEY (`BookID`) REFERENCES `Books` (`BookID`)
) ENGINE=InnoDB AUTO_INCREMENT=7 DEFAULT CHARSET=utf8mb4 COLLATE=utf8mb4_0900_ai_ci;
/*!40101 SET character_set_client = @saved_cs_client */;

--
-- Dumping data for table `BorrowedBooks`
--

LOCK TABLES `BorrowedBooks` WRITE;
/*!40000 ALTER TABLE `BorrowedBooks` DISABLE KEYS */;
INSERT INTO `BorrowedBooks` VALUES (1,1,3,'2024-03-01','2024-03-10'),(2,2,1,'2024-03-05',NULL),(3,3,2,'2024-03-07','2024-03-14'),(4,4,4,'2024-03-10',NULL),(5,5,5,'2024-03-12','2024-03-20'),(6,6,6,'2024-03-17',NULL);
/*!40000 ALTER TABLE `BorrowedBooks` ENABLE KEYS */;
UNLOCK TABLES;

--
-- Table structure for table `Members`
--

DROP TABLE IF EXISTS `Members`;
/*!40101 SET @saved_cs_client     = @@character_set_client */;
/*!50503 SET character_set_client = utf8mb4 */;
CREATE TABLE `Members` (
  `MemberID` int NOT NULL AUTO_INCREMENT,
  `Name` varchar(255) NOT NULL,
  `Email` varchar(255) NOT NULL,
  `Phone` varchar(20) DEFAULT NULL,
  PRIMARY KEY (`MemberID`),
  UNIQUE KEY `Email` (`Email`)
) ENGINE=InnoDB AUTO_INCREMENT=7 DEFAULT CHARSET=utf8mb4 COLLATE=utf8mb4_0900_ai_ci;
/*!40101 SET character_set_client = @saved_cs_client */;

--
-- Dumping data for table `Members`
--

LOCK TABLES `Members` WRITE;
/*!40000 ALTER TABLE `Members` DISABLE KEYS */;
INSERT INTO `Members` VALUES (1,'Alice Johnson','alice@example.com','123-456-7890'),(2,'Bob Smith','bob@example.com','987-654-3210'),(3,'Charlie Brown','charlie@example.com','456-789-0123'),(4,'David Williams','david@example.com','321-654-0987'),(5,'Emily Davis','emily@example.com','789-012-3456'),(6,'kalyan','kalyan@example.com','765-890-1234');
/*!40000 ALTER TABLE `Members` ENABLE KEYS */;
UNLOCK TABLES;
/*!40103 SET TIME_ZONE=@OLD_TIME_ZONE */;

/*!40101 SET SQL_MODE=@OLD_SQL_MODE */;
/*!40014 SET FOREIGN_KEY_CHECKS=@OLD_FOREIGN_KEY_CHECKS */;
/*!40014 SET UNIQUE_CHECKS=@OLD_UNIQUE_CHECKS */;
/*!40101 SET CHARACTER_SET_CLIENT=@OLD_CHARACTER_SET_CLIENT */;
/*!40101 SET CHARACTER_SET_RESULTS=@OLD_CHARACTER_SET_RESULTS */;
/*!40101 SET COLLATION_CONNECTION=@OLD_COLLATION_CONNECTION */;
/*!40111 SET SQL_NOTES=@OLD_SQL_NOTES */;

-- Dump completed on 2025-04-20 12:46:01
