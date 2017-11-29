-- Adminer 4.2.3 MySQL dump

SET NAMES utf8;
SET time_zone = '+00:00';
SET foreign_key_checks = 0;
SET sql_mode = 'NO_AUTO_VALUE_ON_ZERO';

DROP TABLE IF EXISTS `ea_appointments`;
CREATE TABLE `ea_appointments` (
  `id` bigint(20) unsigned NOT NULL AUTO_INCREMENT,
  `book_datetime` datetime DEFAULT NULL,
  `start_datetime` datetime DEFAULT NULL,
  `end_datetime` datetime DEFAULT NULL,
  `notes` text,
  `hash` text,
  `is_unavailable` tinyint(4) DEFAULT '0',
  `id_users_provider` bigint(20) unsigned DEFAULT NULL,
  `id_users_customer` bigint(20) unsigned DEFAULT NULL,
  `id_services` bigint(20) unsigned DEFAULT NULL,
  `id_google_calendar` text,
  PRIMARY KEY (`id`),
  KEY `id_users_customer` (`id_users_customer`),
  KEY `id_services` (`id_services`),
  KEY `id_users_provider` (`id_users_provider`),
  CONSTRAINT `ea_appointments_ibfk_2` FOREIGN KEY (`id_users_customer`) REFERENCES `ea_users` (`id`) ON DELETE CASCADE ON UPDATE CASCADE,
  CONSTRAINT `ea_appointments_ibfk_3` FOREIGN KEY (`id_services`) REFERENCES `ea_services` (`id`) ON DELETE CASCADE ON UPDATE CASCADE,
  CONSTRAINT `ea_appointments_ibfk_4` FOREIGN KEY (`id_users_provider`) REFERENCES `ea_users` (`id`) ON DELETE CASCADE ON UPDATE CASCADE
) ENGINE=InnoDB DEFAULT CHARSET=utf8;

INSERT INTO `ea_appointments` (`id`, `book_datetime`, `start_datetime`, `end_datetime`, `notes`, `hash`, `is_unavailable`, `id_users_provider`, `id_users_customer`, `id_services`, `id_google_calendar`) VALUES
(67,	'2017-11-27 11:02:39',	'2017-11-27 12:00:00',	'2017-11-27 13:00:00',	'',	'2210901c09aed8dc3fbd435fd35b90ed',	0,	88,	89,	14,	NULL),
(68,	'2017-11-27 13:29:11',	'2017-11-27 16:00:00',	'2017-11-27 17:00:00',	'',	'1373d69138fefa36f03b063dd929a64c',	0,	88,	90,	14,	NULL),
(69,	'2017-11-27 13:36:37',	'2017-11-28 09:30:00',	'2017-11-28 10:30:00',	'',	'9207b688ab8c1dd78df7f3873b3e77b6',	0,	88,	89,	14,	NULL),
(70,	'2017-11-28 02:47:21',	'2017-11-28 13:00:00',	'2017-11-28 14:00:00',	'',	'e1f5ea35093ffc34c17f733749a64ffe',	0,	88,	91,	14,	NULL);

DROP TABLE IF EXISTS `ea_roles`;
CREATE TABLE `ea_roles` (
  `id` bigint(20) unsigned NOT NULL AUTO_INCREMENT,
  `name` varchar(256) DEFAULT NULL,
  `slug` varchar(256) DEFAULT NULL,
  `is_admin` tinyint(4) DEFAULT NULL COMMENT '0',
  `appointments` int(4) DEFAULT NULL COMMENT '0',
  `customers` int(4) DEFAULT NULL COMMENT '0',
  `services` int(4) DEFAULT NULL COMMENT '0',
  `users` int(4) DEFAULT NULL COMMENT '0',
  `system_settings` int(4) DEFAULT NULL COMMENT '0',
  `user_settings` int(11) DEFAULT NULL,
  PRIMARY KEY (`id`)
) ENGINE=InnoDB DEFAULT CHARSET=utf8;

INSERT INTO `ea_roles` (`id`, `name`, `slug`, `is_admin`, `appointments`, `customers`, `services`, `users`, `system_settings`, `user_settings`) VALUES
(1,	'Administrator',	'admin',	1,	15,	15,	15,	15,	15,	15),
(2,	'Provider',	'provider',	0,	15,	15,	0,	0,	0,	15),
(3,	'Customer',	'customer',	0,	0,	0,	0,	0,	0,	0),
(4,	'Secretary',	'secretary',	0,	15,	15,	0,	0,	0,	15);

DROP TABLE IF EXISTS `ea_secretaries_providers`;
CREATE TABLE `ea_secretaries_providers` (
  `id_users_secretary` bigint(20) unsigned NOT NULL,
  `id_users_provider` bigint(20) unsigned NOT NULL,
  PRIMARY KEY (`id_users_secretary`,`id_users_provider`),
  KEY `fk_ea_secretaries_providers_1` (`id_users_secretary`),
  KEY `fk_ea_secretaries_providers_2` (`id_users_provider`),
  CONSTRAINT `fk_ea_secretaries_providers_1` FOREIGN KEY (`id_users_secretary`) REFERENCES `ea_users` (`id`) ON DELETE CASCADE ON UPDATE CASCADE,
  CONSTRAINT `fk_ea_secretaries_providers_2` FOREIGN KEY (`id_users_provider`) REFERENCES `ea_users` (`id`) ON DELETE CASCADE ON UPDATE CASCADE
) ENGINE=InnoDB DEFAULT CHARSET=latin1;


DROP TABLE IF EXISTS `ea_services`;
CREATE TABLE `ea_services` (
  `id` bigint(20) unsigned NOT NULL AUTO_INCREMENT,
  `name` varchar(256) DEFAULT NULL,
  `duration` int(11) DEFAULT NULL,
  `price` decimal(10,2) DEFAULT NULL,
  `currency` varchar(32) DEFAULT NULL,
  `description` text,
  `availabilities_type` varchar(32) DEFAULT 'flexible',
  `attendants_number` int(11) DEFAULT '1',
  `id_service_categories` bigint(20) unsigned DEFAULT NULL,
  PRIMARY KEY (`id`),
  KEY `id_service_categories` (`id_service_categories`),
  CONSTRAINT `ea_services_ibfk_1` FOREIGN KEY (`id_service_categories`) REFERENCES `ea_service_categories` (`id`) ON DELETE SET NULL ON UPDATE CASCADE
) ENGINE=InnoDB DEFAULT CHARSET=utf8;

INSERT INTO `ea_services` (`id`, `name`, `duration`, `price`, `currency`, `description`, `availabilities_type`, `attendants_number`, `id_service_categories`) VALUES
(14,	'Interview Schedular',	60,	0.00,	'INR',	'',	'flexible',	1,	NULL);

DROP TABLE IF EXISTS `ea_services_providers`;
CREATE TABLE `ea_services_providers` (
  `id_users` bigint(20) unsigned NOT NULL,
  `id_services` bigint(20) unsigned NOT NULL,
  PRIMARY KEY (`id_users`,`id_services`),
  KEY `id_services` (`id_services`),
  CONSTRAINT `ea_services_providers_ibfk_1` FOREIGN KEY (`id_users`) REFERENCES `ea_users` (`id`) ON DELETE CASCADE ON UPDATE CASCADE,
  CONSTRAINT `ea_services_providers_ibfk_2` FOREIGN KEY (`id_services`) REFERENCES `ea_services` (`id`) ON DELETE CASCADE ON UPDATE CASCADE
) ENGINE=InnoDB DEFAULT CHARSET=utf8;

INSERT INTO `ea_services_providers` (`id_users`, `id_services`) VALUES
(88,	14);

DROP TABLE IF EXISTS `ea_service_categories`;
CREATE TABLE `ea_service_categories` (
  `id` bigint(20) unsigned NOT NULL AUTO_INCREMENT,
  `name` varchar(256) DEFAULT NULL,
  `description` text,
  PRIMARY KEY (`id`)
) ENGINE=InnoDB DEFAULT CHARSET=utf8;


DROP TABLE IF EXISTS `ea_settings`;
CREATE TABLE `ea_settings` (
  `id` bigint(20) unsigned NOT NULL AUTO_INCREMENT,
  `name` varchar(512) DEFAULT NULL,
  `value` longtext,
  PRIMARY KEY (`id`)
) ENGINE=InnoDB DEFAULT CHARSET=utf8;

INSERT INTO `ea_settings` (`id`, `name`, `value`) VALUES
(16,	'company_working_plan',	'{\"monday\":{\"start\":\"09:00\",\"end\":\"18:00\",\"breaks\":[{\"start\":\"11:20\",\"end\":\"11:30\"},{\"start\":\"14:30\",\"end\":\"15:00\"}]},\"tuesday\":{\"start\":\"09:00\",\"end\":\"18:00\",\"breaks\":[{\"start\":\"11:20\",\"end\":\"11:30\"},{\"start\":\"14:30\",\"end\":\"15:00\"}]},\"wednesday\":{\"start\":\"09:00\",\"end\":\"18:00\",\"breaks\":[{\"start\":\"11:20\",\"end\":\"11:30\"},{\"start\":\"14:30\",\"end\":\"15:00\"}]},\"thursday\":{\"start\":\"09:00\",\"end\":\"18:00\",\"breaks\":[{\"start\":\"11:20\",\"end\":\"11:30\"},{\"start\":\"14:30\",\"end\":\"15:00\"}]},\"friday\":{\"start\":\"09:00\",\"end\":\"18:00\",\"breaks\":[{\"start\":\"11:20\",\"end\":\"11:30\"},{\"start\":\"14:30\",\"end\":\"15:00\"}]},\"saturday\":{\"start\":\"09:00\",\"end\":\"18:00\",\"breaks\":[{\"start\":\"11:20\",\"end\":\"11:30\"},{\"start\":\"14:30\",\"end\":\"15:00\"}]},\"sunday\":{\"start\":\"09:00\",\"end\":\"18:00\",\"breaks\":[{\"start\":\"11:20\",\"end\":\"11:30\"},{\"start\":\"14:30\",\"end\":\"15:00\"}]}}'),
(17,	'book_advance_timeout',	'30'),
(18,	'google_analytics_code',	''),
(19,	'customer_notifications',	'1'),
(20,	'date_format',	'DMY'),
(21,	'require_captcha',	'0'),
(22,	'company_name',	'QA Infotech'),
(23,	'company_email',	'ravi.kant@qainfotech.com'),
(24,	'company_link',	'ravi.kant@qainfotech.com');

DROP TABLE IF EXISTS `ea_users`;
CREATE TABLE `ea_users` (
  `id` bigint(20) unsigned NOT NULL AUTO_INCREMENT,
  `first_name` varchar(256) DEFAULT NULL,
  `last_name` varchar(512) DEFAULT NULL,
  `email` varchar(512) DEFAULT NULL,
  `mobile_number` varchar(128) DEFAULT NULL,
  `phone_number` varchar(128) DEFAULT NULL,
  `address` varchar(256) DEFAULT NULL,
  `city` varchar(256) DEFAULT NULL,
  `state` varchar(128) DEFAULT NULL,
  `zip_code` varchar(64) DEFAULT NULL,
  `notes` text,
  `id_roles` bigint(20) unsigned NOT NULL,
  PRIMARY KEY (`id`),
  KEY `id_roles` (`id_roles`),
  CONSTRAINT `ea_users_ibfk_1` FOREIGN KEY (`id_roles`) REFERENCES `ea_roles` (`id`) ON DELETE CASCADE ON UPDATE CASCADE
) ENGINE=InnoDB DEFAULT CHARSET=utf8;

INSERT INTO `ea_users` (`id`, `first_name`, `last_name`, `email`, `mobile_number`, `phone_number`, `address`, `city`, `state`, `zip_code`, `notes`, `id_roles`) VALUES
(84,	'Ravi',	'Kant',	'ravi.kant@qainfotech.com',	NULL,	'9911595115',	NULL,	NULL,	NULL,	NULL,	NULL,	1),
(88,	'Narendra',	'Kumar',	'narendrakumar@qainfotech.com',	'',	'9900000000',	'',	'',	'',	'',	'',	2),
(89,	'abc',	'abc',	'narendrakumar@qainfotech.com',	NULL,	'9900000000',	'',	'',	NULL,	'',	NULL,	3),
(90,	'ajit',	'kumar',	'ajitkumar@qainfotech.com',	NULL,	'99000909090',	'',	'',	NULL,	'',	NULL,	3),
(91,	'aa',	'aa',	'aa@aa.com',	NULL,	'3454354',	'',	'',	NULL,	'',	NULL,	3);

DROP TABLE IF EXISTS `ea_user_settings`;
CREATE TABLE `ea_user_settings` (
  `id_users` bigint(20) unsigned NOT NULL,
  `username` varchar(256) DEFAULT NULL,
  `password` varchar(512) DEFAULT NULL,
  `salt` varchar(512) DEFAULT NULL,
  `working_plan` text,
  `notifications` tinyint(4) DEFAULT '0',
  `google_sync` tinyint(4) DEFAULT '0',
  `google_token` text,
  `google_calendar` varchar(128) DEFAULT NULL,
  `sync_past_days` int(11) DEFAULT '5',
  `sync_future_days` int(11) DEFAULT '5',
  `calendar_view` varchar(32) DEFAULT 'default',
  PRIMARY KEY (`id_users`),
  CONSTRAINT `ea_user_settings_ibfk_1` FOREIGN KEY (`id_users`) REFERENCES `ea_users` (`id`) ON DELETE CASCADE ON UPDATE CASCADE
) ENGINE=InnoDB DEFAULT CHARSET=utf8;

INSERT INTO `ea_user_settings` (`id_users`, `username`, `password`, `salt`, `working_plan`, `notifications`, `google_sync`, `google_token`, `google_calendar`, `sync_past_days`, `sync_future_days`, `calendar_view`) VALUES
(84,	'admin',	'6c279efe1389535a88e6110a1c0a9689603cc394d90ded8ee3956fde0dff108a',	'8671757f1eb0c44f13a0264d916b385239f5078c1fe05aa05e6c23af9b5564d4',	NULL,	0,	0,	NULL,	NULL,	5,	5,	'default'),
(88,	'narendra',	'82fb8efd6ea5803883fa6d27ef7275756c93c5b8caefb620e080cb4e8e537880',	'55eed763a2080146edf5300ec8d8bdd1a86f8ab8598cccbce54da546a42379a0',	'{\"monday\":{\"start\":\"09:00\",\"end\":\"18:00\",\"breaks\":[{\"start\":\"11:20\",\"end\":\"11:30\"},{\"start\":\"14:30\",\"end\":\"15:00\"}]},\"tuesday\":{\"start\":\"09:00\",\"end\":\"18:00\",\"breaks\":[{\"start\":\"11:20\",\"end\":\"11:30\"},{\"start\":\"14:30\",\"end\":\"15:00\"}]},\"wednesday\":{\"start\":\"09:00\",\"end\":\"18:00\",\"breaks\":[{\"start\":\"11:20\",\"end\":\"11:30\"},{\"start\":\"14:30\",\"end\":\"15:00\"}]},\"thursday\":{\"start\":\"09:00\",\"end\":\"18:00\",\"breaks\":[{\"start\":\"11:20\",\"end\":\"11:30\"},{\"start\":\"14:30\",\"end\":\"15:00\"}]},\"friday\":{\"start\":\"09:00\",\"end\":\"18:00\",\"breaks\":[{\"start\":\"11:20\",\"end\":\"11:30\"},{\"start\":\"14:30\",\"end\":\"15:00\"}]},\"saturday\":{\"start\":\"09:00\",\"end\":\"18:00\",\"breaks\":[{\"start\":\"11:20\",\"end\":\"11:30\"},{\"start\":\"14:30\",\"end\":\"15:00\"}]},\"sunday\":{\"start\":\"09:00\",\"end\":\"18:00\",\"breaks\":[{\"start\":\"11:20\",\"end\":\"11:30\"},{\"start\":\"14:30\",\"end\":\"15:00\"}]}}',	0,	0,	NULL,	NULL,	5,	5,	'default');

-- 2017-11-29 05:13:01
