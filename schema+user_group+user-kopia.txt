CREATE ROLE expense_tracker_user WITH LOGIN PASSWORD 'qwerty123?';
REVOKE CREATE ON SCHEMA public FROM PUBLIC;
DROP SCHEMA IF EXISTS expense_tracker CASCADE;
CREATE ROLE expense_tracker_group;
CREATE SCHEMA expense_tracker AUTHORIZATION expense_tracker_group;
GRANT CONNECT ON DATABASE postgres TO expense_tracker_group;
GRANT ALL PRIVILEGES ON SCHEMA expense_tracker TO expense_tracker_group;
GRANT expense_tracker_group TO expense_tracker_user;